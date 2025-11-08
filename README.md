# Belém — Equatorial, Quente e Úmido

![Imagem final](Resultado/imagem_final.png)

> Visualização climática de Belém (PA) com Python + INMET, celebrando o clima **EQUATORIAL**, **QUENTE** e **ÚMIDO**.  
> A imagem final é uma composição artística feita no GIMP com tipografia paraense.

## Sobre o projeto

Este projeto demonstra como usar **Python** para coletar e preparar dados do **INMET/BDMEP** e gerar visualizações sobre o clima de Belém.
Ele presta uma homenagem ao clima característico da cidade:

- **Equatorial** — A estrela no topo indica a latitude de Belém (~ **1°27'15.90" S**), dimensionada com base em um mapa do **IBGE** usado como referência na composição.
- **Quente** — Curva de **sensação térmica (feels like)** agregada a partir de dados dos **últimos 5 anos**. Destaques: **43 °C (máx)**, **25 °C (mín)** e **32 °C (média histórica)**.
- **Úmido** — Curva de umidade relativa com **98 % (máx)**, **74 % (mín)** e **86 % (média)**.

> **Observação**: As curvas mostram **sensação térmica (feels like)**, não a temperatura do ar convencional.

## Arquitetura de dados

O notebook segue o padrão **Medalhão (Bronze → Silver → Gold)**:

- **Bronze**: ingestão bruta dos dados meteorológicos (BDMEP/INMET).
- **Silver**: limpeza, padronização de colunas, cálculo de *feels like* e ajustes de séries.
- **Gold**: agregações por faixa horária/ano, estatísticas (mín/média/máx) e *features* prontas para visualização.

As visualizações foram criadas com **Matplotlib** e **Seaborn**.
A **composição final** (tipografia/elementos gráficos) foi feita no **GIMP**, para aplicação de fontes regionais personalizadas.

## Estrutura do repositório

```
.
├── Equatorial _ Quente _ Umido.ipynb   # Notebook com todo o código do pipeline/visual
├── Fonts/                              # Fontes usadas na composição (ver licenças específicas)
├── Referencias/                        # Estudos visuais, referências e rascunhos
└── Resultado/
    ├── imagem_final.png                # Peça final (composição no GIMP)
    ├── imagem_original_python.png      # Export direto do Python (antes do GIMP)
    └── projeto_gimp.xcf                # Arquivo .xcf do GIMP (camadas/fontes)
```

## Como reproduzir

### 1) Obter dados do INMET (BDMEP)
- Portal: https://bdmep.inmet.gov.br/ (BDMEP – Banco de Dados Meteorológicos para Ensino e Pesquisa).
- O acesso exige cadastro. Baixe as séries para Belém referentes aos **últimos 5 anos**.
- Salve os arquivos numa pasta acessível pelo notebook (o próprio notebook indica onde colocá-los).

### 2) Ambiente local (opção)
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -U pip
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook "Equatorial _ Quente _ Umido.ipynb"
```

### 3) Databricks (opção)
1. Importe o notebook `Equatorial _ Quente _ Umido.ipynb` para seu Workspace.
2. Use um cluster com Runtime recente (inclua `matplotlib` e `seaborn`).
3. Aponte os caminhos dos dados (Bronze) no notebook.
4. Execute as células Bronze → Silver → Gold → Visual.

### 4) Geração do visual e composição
- O notebook exporta `Resultado/imagem_original_python.png`.
- Abra `Resultado/projeto_gimp.xcf` no GIMP para aplicar as fontes de **Fonts/** e compor a arte final (estrela, títulos “Equatorial / Quente / Úmido”, etc.).
- Exporte `Resultado/imagem_final.png` (também destacada no topo deste README).

## Fontes e créditos

- **Dados meteorológicos**: INMET/BDMEP — https://bdmep.inmet.gov.br/
- **Mapa de referência para latitude**: IBGE (utilizado para dimensionamento/posicionamento da estrela na seção “Equatorial”).
- **Tipografia**: ver diretório `Fonts/` e o arquivo **FONTS-LICENSES.md** (cada fonte possui sua própria licença).
- **Código**: MIT (ver `LICENSE`).
- **Imagens/arte do repositório**: CC BY 4.0 (ver `ASSETS-LICENSE.md`).

## Licenças

- **Código**: [MIT](LICENSE)
- **Assets visuais (imagens, layouts, mockups)**: [CC BY 4.0](ASSETS-LICENSE.md) — permite **qualquer modificação**, inclusive uso comercial, com **atribuição**.
- **Fontes**: licenças próprias do(s) autor(es). Veja `FONTS-LICENSES.md` e mantenha os arquivos de licença de cada fonte.

## Contribuindo

1. Abra uma *issue* descrevendo melhorias/bugs.
2. Para PRs, siga o estilo do notebook e descreva claramente o passo da camada (Bronze/Silver/Gold) que foi alterado.
3. Evite commitar dados brutos do INMET que estejam sob termos específicos de uso.

## Autor

Feito por **Arnold Souza** — projeto Belém Chuva.
