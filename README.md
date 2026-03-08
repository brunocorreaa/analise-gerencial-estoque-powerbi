# Dashboard de Visão Gerencial de Estoque

## 📌 Sobre o Projeto

Este projeto consiste em um dashboard interativo desenvolvido no **Power BI** para fornecer uma análise estratégica e granular do estoque de uma rede de varejo.

O objetivo central é monitorar a saúde do estoque através de KPIs-chave (como cobertura e giro), analisar a idade do estoque (aging) por setor específico e comparar a eficiência do giro de produtos novos versus antigos, permitindo decisões rápidas para otimização de capital de giro e prevenção de rupturas de estoque.

### 💡 Por que este projeto é importante?

A gestão de estoque eficiente é a coluna vertebral de um varejo saudável. Este dashboard traz transparência para as seguintes questões críticas de negócio:

* **Liberação de Capital de Giro:** Identifica produtos parados por muito tempo (estoque antigo), permitindo ações de desconto ou redistribuição estratégica para liberar capital para novas compras.
* **Apoio a Decisões de Compra:** KPIs claros de `Cobertura` e `Giro` ajudam gestores a entender quais produtos estão operando próximos ao fim de estoque e precisam de reabastecimento imediato.
* **Redução de Perdas:** Permite uma visão clara da `Idade do Estoque (Aging)`, fundamental para setores com perecíveis ou bens de consumo de giro rápido, evitando o envelhecimento excessivo de produtos na prateleira.
* **Benchmarking Setorial:** Compara o desempenho de diferentes setores da loja, identificando quais estão com excesso de estoque e quais estão operando com eficiência.

---

## 🛡️ Disclaimer e Privacidade (Dados Anonimizados)

Para fins de exibição pública e proteção de dados sensíveis:
* **Anonimização:** Todos os dados de vendas, custos, volumetria de peças e identificação de filiais foram alterados para dados sintéticos/fictícios, mantendo a integridade técnica da lógica.
* **Nomenclatura:** Os nomes das tabelas fato (`fVendas`, `fEstoque`) e tabelas dimensão (`dProdutos`, `dFiliais`), bem como variáveis técnicas e medidas calculadas (`Estoque Custo`, `Cobertura`, etc.), foram renomeados ou simplificados para abstrair a propriedade intelectual do negócio original, mantendo-se fiel à lógica funcional do dashboard.

---

## 🏗️ Estrutura de Dados e Relacionamentos

A modelagem de dados segue as melhores práticas de Business Intelligence, utilizando um esquema estrela que conecta tabelas fato e dimensão de forma otimizada para performance.

<img width="731" height="687" alt="modelo-dados" src="https://github.com/user-attachments/assets/6b48e77f-1ad1-46f9-a263-cee7db2efeed" />

*Figura 1: Esquema de Dados e Relacionamentos de Estoque.*

### Entidades do Modelo:

* **fVendas (Fato):** Centraliza métricas de movimentação de vendas (Data, Filial, Produto, Qtd_Venda, Venda_Custo, Venda_Liquido).
* **fEstoque (Fato):** Centraliza métricas de saldo de estoque (Data, Filial, Produto, Estoque_Custo, Qtd_Estoque).
* **dProdutos (Dimensão):** Cadastro de produtos (Produto, Classe, Grupo, Idade do Estoque, Setor, Subclasse).
* **dFiliais (Dimensão):** Atributos geográficos e cadastrais das unidades de negócio.
* **_Medidas (Tabela de Medidas):** Centraliza todas as regras de negócio escritas em DAX (`Cobertura`, `Estoque Custo`).

---

## 🛠️ Detalhes das Visões (Relatório Power BI)

O relatório é dividido em duas visões principais para permitir uma análise macro (Filial) e micro (Setor).

### 1. Visão Geral: KPIs de Saúde do Estoque e Aging por Setor

Esta visão apresenta KPIs claros e uma quebra granular da idade do estoque por setor.

**Destaques:**
* **Painel de KPIs:** Cards que mostram os totais agregados para `Venda Custo`, `Estoque Custo`, `Qtd de Venda`, `Estoque Qtd`, e indicadores críticos como `Cobertura` (quantos dias de estoque) e `Giro` (quantas vezes o estoque girou).
* **Participação da Idade do Estoque por Setor:** Um gráfico de barras empilhadas 100% que mostra o percentual de estoque por faixa de idade (`01.30dd`, `02.90dd`, etc.) para cada setor (A a F).
* **Insight:** Permite identificar rapidamente quais setores têm uma participação excessiva de estoque antigo (`>270 dd` ou `>360 dd`), facilitando o direcionamento operacional.

<img width="1442" height="809" alt="visao-geral" src="https://github.com/user-attachments/assets/1ec4dc53-66a6-45ae-9dee-7898f8281224" />

*Figura 2: Painel de KPIs e Aging Setorial.*

### 2. Visão Detalhada: Eficiência do Giro por Idade do Estoque

Esta visão foca no desempenho granulado por categoria ou setor de loja, permitindo identificar quais áreas específicas estão subdimensionadas.

**Destaque:**
* **Análise de Margem e Giro:** Gráficos que mostram o custo de venda (azul escuro) versus o custo de estoque (azul claro) segmentado pelas mesmas faixas etárias de estoque.
