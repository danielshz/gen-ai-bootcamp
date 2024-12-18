# 🚀 Text-to-SQL Generator - Projeto Final VAI Academy

Este repositório contém a implementação do projeto final do Bootcamp de IA Generativa da VAI Academy. O objetivo principal foi desenvolver um sistema que interpreta perguntas em linguagem natural e as traduz para consultas SQL, facilitando a análise de grandes volumes de dados provenientes de sensores telemétricos de máquinas.

## 🧩 Contexto

Empresas que utilizam telemetria para monitorar máquinas frequentemente enfrentam desafios para transformar os dados em insights acionáveis. Essas máquinas enviam medições em tempo real, que são armazenadas em bases de dados para posterior análise. A interpretação dessas informações exige esforço manual de analistas para elaborar relatórios e responder a questões específicas.

A solução proposta utiliza um modelo de **Text-to-SQL**, permitindo aos analistas ou clientes fazer perguntas diretamente em linguagem natural e receber como resposta a consulta SQL correspondente e a resposta esperada. Isso reduz o tempo e o esforço necessários para gerar relatórios e analisar dados.

## ⚙️ Funcionalidades Principais

O sistema implementa um pipeline completo para a geração e execução de consultas SQL, com os seguintes componentes:

### 1. Guardrails 🛡️
- Filtra e ajusta a pergunta do usuário para garantir que está no contexto do banco de dados.
- Gera uma versão resumida e ajustada da pergunta, facilitando etapas posteriores.

### 2. Selector 🎯
- Seleciona tabelas e colunas relevantes com base na pergunta e no esquema do banco de dados.
- Cria visualizações filtradas dos dados, alinhadas ao contexto da consulta.

### 3. Decomposer 🧮
- Gera consultas SQL utilizando duas abordagens:
  - **Divide and Conquer CoT**: Divide a pergunta em sub-problemas menores e resolve cada um separadamente.
  - **Query Plan CoT**: Baseia-se em um plano de consulta estruturado, com três etapas principais.

### 4. Refiner 🔧
- Valida e corrige erros nas consultas SQL geradas, incluindo erros de sintaxe e execução.
- Utiliza um loop iterativo com histórico de erros para refinamento contínuo, garantindo que as consultas finais sejam executáveis.

### 5. Juror 🏛️
- Avalia as consultas SQL geradas e os resultados obtidos.
- Seleciona a consulta mais adequada e converte os resultados em respostas humanamente legíveis.

### 6. Sistema Completo 🔗
- Integra todos os componentes em um fluxo único, transformando perguntas em linguagem natural em respostas SQL e textuais.

### 7. Testes 🧪
- O notebook inclui cenários de teste que demonstram o fluxo completo do sistema, incluindo tratamento de erros e execução de consultas em diferentes contextos.

## 🛠️ Tecnologias Utilizadas

- **SQLite**: Gerenciamento do banco de dados.
- **Pandas**: Manipulação dos dados fornecidos (e.g., arquivos Excel).
- **LangChain**: Integração com modelos de linguagem para processamento de entradas e saídas.
- **LLM Gemini 1.5 Flash**: Modelo escolhido por sua eficiência em tarefas de baixa complexidade, baixo custo e alta velocidade.

## 📊 Dados Utilizados

A base de dados é composta por:
1. **Telemetria**: Informações enviadas pelos sensores das máquinas.
2. **Chassis**: Dados sobre os chassis das máquinas, como modelo e cliente associado.
3. **Glossário**: Descrições das colunas e categorias presentes nos dados.

Esses dados foram utilizados para construir um sistema que realiza consultas eficientes e retorna respostas relevantes para questões específicas.

## ✅ Métricas de Validação

Para avaliar o desempenho do sistema, foram utilizadas as seguintes métricas:
- **Similaridade de Cossenos**: Mede a proximidade semântica entre a consulta SQL gerada e a esperada.
- **ROGUE**: Avalia a capacidade de sumarizar informações textuais.
- **Verificação Humana**: Assegura que as respostas geradas fazem sentido e atendem ao contexto da pergunta.

## 🎉 Benefícios para o Cliente

A solução oferece:
1. **Automatização de Consultas SQL**: Reduzindo a necessidade de interação manual com o banco de dados.
2. **Otimização de Tempo**: Processamento mais rápido e preciso de perguntas complexas.
3. **Insights Diretos**: Geração de relatórios com informações relevantes de forma automatizada.
