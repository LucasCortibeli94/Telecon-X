# Telecon-X


Projeto do desafio **Telecom X** (Programa ONE + Alura) com foco em **ETL (Extract, Transform, Load)** e **EDA (Análise Exploratória)** para compreender fatores associados ao **churn** (evasão de clientes).

---

## 🎯 Objetivo
- **Extract:** obter os dados via API (JSON hospedado no GitHub).
- **Transform:** normalizar campos aninhados, tratar tipos/ausentes e criar variáveis derivadas.
- **Load:** disponibilizar um dataset limpo para análises e modelagem.
- **EDA:** extrair insights iniciais para orientar ações de retenção.

---

## 🗂️ Estrutura do Repositório
.
├── {NOTEBOOK_FILE} # Notebook principal (ETL + EDA + relatório)
├── README.md
├── data/
│ ├── raw/
│ │ └── TelecomX_Data.json # (Opcional) cópia bruta da fonte
│ └── processed/
│ └── telecomx_tratado.csv # Base tratada (gerada no notebook)
└── img/ # (Opcional) gráficos exportados para o README
├── churn_distribuicao.png
├── churn_por_contrato.png
└── churn_por_tenure.png

yaml
Copiar
Editar

---

## 🔄 Processo ETL (resumo)
1. **Extração:** leitura do JSON “raw” diretamente do GitHub.
2. **Transformação:**
   - `pd.json_normalize()` para “achatar” campos aninhados (`customer`, `phone`, `internet`, `account`).
   - Padronização de nomes (snake_case).
   - Conversão de tipos numéricos (ex.: `account_charges_total`).
   - *Features* derivadas (ex.: `annual_revenue`, `customer_tenure_group`).
3. **Carga:** salvamento do dataset limpo em `data/processed/telecomx_tratado.csv`.

---

## ▶️ Como executar

### Opção 1 — Google Colab (recomendado)
1. Clique no badge **Open in Colab** no topo ou abra o notebook no Colab.
2. Execute as células na ordem **Extração → Transformação → Carga & Análise → Relatório**.

### Opção 2 — Local (Jupyter/VSCode)
```bash
python -m venv .venv
# Windows: .venv\\Scripts\\activate
# Linux/Mac:
source .venv/bin/activate

pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook
# Abra o notebook {NOTEBOOK_FILE} e execute
📈 Principais Resultados (EDA)
Dimensões: 7.267 clientes × 23 colunas
Taxa de Churn: ~26,54% (Yes) vs 73,46% (No)

Pontos-chave:

Contrato: Month-to-month concentra mais churn; contratos de 1–2 anos retêm melhor.

Tenure: churn mais alto nos primeiros 12 meses; fidelização cresce com o tempo.

Preço: quem churnou tende a ter mensalidade maior.

Pagamento: Electronic check aparece mais associado ao churn do que métodos automáticos.

Exporte gráficos e adicione na pasta img/ para ilustrar:

python
Copiar
Editar
plt.savefig("img/churn_por_contrato.png", dpi=150, bbox_inches="tight")
🧭 Recomendações
Migrar clientes mensais para planos com fidelização (descontos/benefícios).

Onboarding proativo nos 6–12 meses iniciais (tutoriais, bônus, check-ins).

Planos intermediários/bundles para fibra/alto ticket.

Incentivar pagamento automático (desconto) para reduzir churn ligado a electronic check.

🧰 Tecnologias
Python • Pandas • NumPy • Matplotlib • Seaborn • Google Colab/Jupyter • Git & GitHub

👤 Autor
Projeto desenvolvido por Lucas Cortibeli no desafio Telecom X (Programa ONE + Alura).
"""

with open("README.md", "w", encoding="utf-8") as f:
f.write(readme)

print("README.md criado na raiz do Colab. Baixe pelo painel de arquivos (lado esquerdo) e envie ao GitHub.")

markdown
Copiar
Editar

### Depois de gerar:
- No Colab, abra o painel de arquivos (ícone de pasta à esquerda), clique com o botão direito em **README.md** → **Download**.  
- No GitHub (repo **Telecon-X**), clique em **Add file → Upload files** e envie o `README.md`.  
- (Opcional) Renomeie o notebook no GitHub para `TelecomX_ETL.ipynb` e atualize a variável `NOTEBOOK_FILE` se quiser regenerar o README com link limpo.

Se quiser, também te passo um snippet para **renomear o notebook pelo Git** no próprio Colab e dar `commit/push`.
::contentReference[oaicite:0]{index=0}
