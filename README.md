# jacktrip-apt

Repositório APT para o JackTrip, com builds automáticos diários.

Este repositório fornece pacotes `.deb` do [JackTrip](https://github.com/jacktrip/jacktrip) para distribuições baseadas em Debian (Debian 12+, Ubuntu 22.04+).  
Os pacotes são compilados automaticamente sempre que o JackTrip lança uma nova versão, e são disponibilizados tanto num repositório APT (via GitHub Pages) como em Releases do GitHub.

---

## 📦 Instalação via APT (recomendado)

### 1. Importar a chave GPG

```bash
sudo mkdir -p /etc/apt/keyrings
wget -qO- https://raw.githubusercontent.com/tiagocasalribeiro/jacktrip-apt/main/public.key | sudo gpg --dearmor -o /etc/apt/keyrings/jacktrip-archive-keyring.gpg
```

### 2. Adicionar o repositório

```bash
echo "deb [signed-by=/etc/apt/keyrings/jacktrip-archive-keyring.gpg arch=amd64] https://tiagocasalribeiro.github.io/jacktrip-apt stable main" | sudo tee /etc/apt/sources.list.d/jacktrip.list
```

### 3. Atualizar e instalar

```bash
sudo apt update
sudo apt install jacktrip
```

---

## 🔽 Instalação manual (`.deb`)

Se preferir, pode descarregar o pacote `.deb` diretamente da [página de Releases](https://github.com/tiagocasalribeiro/jacktrip-apt/releases).

```bash
wget https://github.com/tiagocasalribeiro/jacktrip-apt/releases/download/vX.Y.Z/jacktrip_X.Y.Z-1_amd64.deb
sudo dpkg -i jacktrip_*.deb
sudo apt install -f   # instala dependências em falta
```

---

## 🔧 Como funciona o build automático

O repositório contém um workflow GitHub Actions que:

- Verifica diariamente (06:00 UTC) se há uma nova release no [jacktrip/jacktrip](https://github.com/jacktrip/jacktrip).
- Se existir, faz o download do código-fonte, compila o `.deb` num container Debian 12 (Bookworm) com todas as dependências necessárias (Qt6, JACK, etc.).
- Publica o pacote no repositório APT (branch `gh-pages`) e cria uma Release no GitHub com o `.deb` anexado.

O repositório APT é assinado com GPG, garantindo autenticidade e segurança.

---

## ✅ Compatibilidade

Os pacotes são compilados com **Debian 12 (Bookworm)** e **Qt6**, sendo compatíveis com:

- Debian 12 (Bookworm) e 13 (Trixie)
- Ubuntu 22.04 LTS (Jammy) e 24.04 LTS (Noble)
- Derivados baseados nestas versões (Linux Mint, Pop!_OS, etc.)

> **Nota**: Não são compatíveis com Debian 11 ou Ubuntu 20.04 (versões mais antigas não têm Qt6 disponível).

---

## 📄 Licença

Este repositório contém apenas os ficheiros de empacotamento. O JackTrip é licenciado sob a [GPL-2.0](https://github.com/jacktrip/jacktrip/blob/main/LICENSE).