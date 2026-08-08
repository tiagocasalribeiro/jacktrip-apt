# jacktrip-apt

Repositório APT automatizado para o [JackTrip](https://github.com/jacktrip/jacktrip).

Este repositório contém os arquivos de empacotamento e o workflow GitHub Actions que, diariamente, verifica se há uma nova release do JackTrip, compila o pacote `.deb` e publica-o tanto num repositório APT (via GitHub Pages) como nas Releases do GitHub.

---

## 📦 Adicionar o repositório APT (assinado)

### 1. Criar o diretório para as chaves (se não existir)

```bash
sudo mkdir -p /etc/apt/keyrings