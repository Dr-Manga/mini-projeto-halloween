# 🎃 Mini-Projeto Avaliativo: Análise e Higienização de Vendas de Halloween

**Curso:** Machine Learning e Visão Computacional (SCTEC - Turma 05)  
**Módulo 1:** Fundamentos de Python e Análise de Dados (Semana 07)  
**Autor:** Gabriel Fernandes (Dr-Manga)  
**Licença:** MIT  

---

## 📌 1. Visão Geral do Projeto

Este projeto tem como objetivo realizar a ingestão, auditoria, higienização e validação analítica de uma base de dados transacional de vendas comemorativas de Halloween (`halloween_vendas.csv`, contendo 1.500 registros e 14 colunas).

O trabalho foi desenvolvido de forma iterativa e incremental, aplicando boas práticas de versionamento de código via Git (Git Flow simplificado por Sprints) e documentação técnica para suporte a tomadas de decisão gerenciais e futuros pipelines de Machine Learning.

---

## 🛠️ 2. Estrutura das Sprints e Versionamento

O repositório foi organizado em branches temáticas que refletem o ciclo de vida da engenharia e análise de dados:

* `main`: Ramo estável com código final higienizado, documentação e relatórios consolidados.
* `feat/sprint1-ingestao`: Leitura do CSV com Pandas, verificação do shape `(1500, 14)` e checagem de tipos de dados.
* `feat/sprint2-limpeza`: Desenvolvimento de funções modulares para padronização de strings:
  * Expressões Regulares (`re.sub`) e tratamento de caracteres especiais/ruídos na coluna `categoria` (categorias finais: *fantasia*, *acessorio* e *sem categoria*).
  * Lógica condicional estruturada para a coluna `canal_venda` (*Web*, *Loja física*, *Mercado*).
* `feat/sprint3-validacao`: Conversão segura para tipos numéricos com `pd.to_numeric(..., errors='coerce')`, auditoria de inconsistências (quantidades $\le 0$ e preços negativos/nulos) e criação do dataset confiável (`df_limpo`, 1.481 linhas).
* `feat/sprint4-datas-negocio`: Investigação da hipótese da gestão (pedidos sem entrega vs. status) e conversão/auditoria de datas de venda via biblioteca `datetime`, identificando a sazonalidade do evento.

---

## 🧠 3. Reflexão Teórica: Qualidade de Dados e Machine Learning

Um dos maiores desafios em projetos de Ciência de Dados e Inteligência Artificial é sintetizado no princípio clássico:

$$\text{"Garbage In, Garbage Out (GIGO)"}$$

1. **Impacto de Ruídos em Algoritmos:** Se modelos de Machine Learning (como regressão de demanda ou agrupamento de clientes) forem treinados com quantidades negativas (ex: `-1`) ou categorias fragmentadas (ex: `FANTASIA!!!` vs `fantasia`), o modelo aprenderá padrões espúrios.
2. **Distribuição e Generalização:** Preços nulos (`NaN`) geram erros fatais em tensores e matrizes de features, exigindo descarte criterioso ou imputação fundamentada. No projeto, o descarte de apenas 1,27% da base (19 registros) garantiu a integridade matemática sem comprometer a representatividade estatística.
3. **Regras de Negócio e Engenharia de Features:** Entender a diferença entre uma falha sistêmica (pedidos entregues sem carimbo de entrega) e um cancelamento real impede que algoritmos de classificação sejam enviesados por rótulos incorretos (*label noise*).

---

## 🚀 4. Como Executar o Projeto

### Pré-requisitos:
* Python 3.10 ou superior
* Bibliotecas: `pandas`, `ipykernel`

### Passo a passo:
```bash
# Clone o repositório
git clone https://github.com/Dr-Manga/mini-projeto-halloween.git

# Acesse o diretório
cd mini-projeto-halloween

# Instale os pacotes necessários
pip install pandas ipykernel

# Abra o Jupyter Notebook ou execute pelo VS Code
meu_projeto.ipynb
```

---

## 📂 5. Estrutura do Repositório

```text
mini-projeto-halloween/
│
├── halloween_vendas.csv     # Base de dados bruta (1.500 linhas)
├── meu_projeto.ipynb        # Caderno executável com todas as etapas e análises
├── report.md                # Relatório executivo de insights (limite de 1.500 a 3.000 caracteres)
├── README.md                # Documentação técnica e reflexão teórica
└── LICENSE                  # Licença aberta MIT
```
