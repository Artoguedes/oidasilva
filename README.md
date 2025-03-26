name: deploy para github pages 

on:
  push:
    branches:
      - main #Executa quando ha mudancas na branch principal

permissions: 
  contents: write
  pages: write
  id-token: write

jobs:
  deploy: 
    runs-on: ubuntu-latest

  steps: 
    - name: checkout do repositorio
      uses: actions/checkout@v4

    - name: configurar github pages
    uses: actions/configure-pages@v5

    -name: criar artefato para deploy
     uses: actions/upload-pages-artifact@v3 #pode tambem v2
     with:
      path: .

    -name: publicar no github pages
    uses: actions/deploy-pages@v4
