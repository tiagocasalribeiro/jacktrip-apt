# jacktrip-apt

Repositório APT automatizado para o [JackTrip](https://github.com/jacktrip/jacktrip).

Este repositório contém os arquivos de empacotamento e o workflow GitHub Actions que, diariamente, verifica se há uma nova release do JackTrip, compila o pacote `.deb` e publica-o tanto num repositório APT (via GitHub Pages) como nas Releases do GitHub.

---

## 📦 Adicionar o repositório APT

```bash
echo "deb [trusted=yes] https://tiagocasalribeiro.github.io/jacktrip-apt stable main" | sudo tee /etc/apt/sources.list.d/jacktrip.list
sudo apt update