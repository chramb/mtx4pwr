---
title: Instrukcja
---

## Przygotowanie Środowiska
Środowisko na którym postawiony zostanie symulowany serwer nie ma zanczenia, w naszej symulacji została wybrana chmura oracle ze względu na plan hostowania tam pełnej usługi w przyszłości. 

### Niezbędne Środowisko

Środowisko wymagane do przeprowadzenia symulacji:

- Maszyna wirtualna z dostępem do internetu oraz możliwym połączeniem z nią protokołem ssh w celu konfiguracji
- Adres DNS skierowany na maszynę wirtualną (można w tym celu wykorzystać usługę [duckdns](https://duckdns.org))
- Maszyna z zainstalowanymi narzędziami 
    - Ansible - w celu konfirguracji serwera
    - Git - w celu pobrania konfiguracji
    - SSH - w celu bezpiecznego połączenia się z serwerem

### Pobranie playbooka z konfiguracją

Konfiguracja jest hostowana na platformie GitHub więc posłużymy się nażędziem Git w celu pozyskania jej
```shell
git clone --recurse-submodules https://github.com/pwr-pro/mtx4pwr.git && cd mtx4pwr/ansible/matrix-docker-ansible-deploy
```

## Przygotowanie konfiguracji
Ponieważ Symulowany serwer będzie miał inny adres IP oraz hasła niezbędna jest wpisanie ich teraz do pobranej konfiguracji


### Konfigurowanie dostępu
w pliku `inventory/hosts` należy wpisać adres naszego serwera oraz niezbędne dane serwera

```toml
[matrix_servers]
<adres DNS serwera> ansible_host=<nazwa hosta dla SSH> ansible_ssh_user=<nazwa użytkownika>
```

W przypadku tej symulacji plik będzie wyglądał następująco:
```toml
[matrix_servers]
matrix.pwr.ambrozy.xyz ansible_host=oci-pwr ansible_ssh_user=ubuntu
```

- `matrix.pwr.ambrozy.xyz` - odnosi się do adresu DNS serwera
- `ansible_host` - odnisi się do nazwy hosta wykorzystywanej przez serwer ssh (przy wykonywaniu komendy `ssh <nazwa hosta>`)
- `ansible_ssh_user` - nazwa użytkownika na serwerze

### Konfigurowanie Usług

następnie w pliku `vars.yml` znajduącym się w `inventory/host_vars/<adres DNS serwera>/vars.yml` należy wypisać następujące zmienne:

```yaml
---
# przykładowa wartość: example.com
matrix_domain: '<bazowa domena dla serwera>'

matrix_homeserver_implementation: synapse

# komenda umożliwiająca wygenerowanie bezpiecznego sekretu: (e.g. `pwgen -s 64 1`).
matrix_homeserver_generic_secret_key: '<sekret serwera domowego>'

matrix_ssl_lets_encrypt_support_email: '<adres email dla usługi letsencrypt>'

devture_postgres_connection_password: '<hasło dla bazy danych>'
matrix_nginx_proxy_base_domain_serving_enabled: true

# architektura serwera
# najprawdopodobniej wymagane będzie usunięcie tej zmiennej 
# przy próbach odtworzenia wyników na serwerach z architekturą amd64/x86_64
matrix_architecture: "arm64" 

# Wyłączenie federacji z innymi serwerami w celu zmniejszenia zużycia zasobów
matrix_synapse_federation_enabled: false
```
## Aplikowanie Konfiguracji
Następnie należy wykonać komendę `ansible-playbook` aplikującą właśnie napisaną konfigurację na serwerze
```shell
ansible-playbook -i inventory/hosts setup.yml --tags=setup-all,start-all
```

Po dłuższej chwili na podanym adresie możemy spodziewać się klienta webowego który za chwilę zostanie wykorzystany do testów.

## Tworzenie użytkownika
Ponieważ symulacja nie obejmuje 3PID stworzymy użytkownika ręcznie, komenda którą się do tego posłużymy to:
```shell
ansible-playbook -i inventory/hosts setup.yml --tags=register-user --extra-vars='username=<nazwa użytkownika> password=<hasło> admin=no'
```

Przy tej symulacji stworzony został użytkownik `test-user`


## Wynik
W wyniku otzymamy następującą konfigurację wszystkich usług:
