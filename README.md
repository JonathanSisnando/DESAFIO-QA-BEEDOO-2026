
## Relatório de Análise Técnica Inicial - Projeto Beedoo QA Challenge

Este documento detalha a avaliação preliminar de qualidade de software para a aplicação de gerenciamento de cursos, focando em interface, funcionalidade básica e experiência do usuário (UX).

### 1. Visão Geral do Sistema
O sistema consiste em uma aplicação web destinada a realizar operações de **CRUD** (Create, Read, Update, Delete) para a entidade "Cursos". A navegação é simplificada, composta por duas telas principais: Listagem e Cadastro.

* **Ambiente:** Produção (Netlify)
* **Escopo:** Validação de Interface (UI), Experiência do Usuário (UX) e Fluxo Funcional Positivo.

### 2. Levantamento de Defeitos e Inconsistências (UI/UX)

#### 2.1 Erros Ortográficos e de Texto
* **Evidência:** No componente de cabeçalho (Header), o título exibe a string "Beedoo QA Chalenge".
* **Análise Técnica:** Há um erro de grafia na palavra "Challenge" (falta do caractere 'l'). Embora a severidade seja considerada **baixa**, o impacto na imagem do produto é direto.

#### 2.2 Ausência de Affordance e Indicadores de Campo
* **Evidência:** O formulário de cadastro não utiliza indicadores visuais de obrigatoriedade (como o caractere `*`) nos labels.
* **Análise Técnica:** A ausência de marcação estática de campos obrigatórios fere as heurísticas de usabilidade, podendo levar o usuário a erros de preenchimento antes mesmo da submissão.

### 3. Validação Funcional (Happy Path)
A verificação do fluxo principal foi concluída com sucesso:
1. **Inserção de Dados:** O formulário aceitou os inputs sem erros de runtime.
2. **Persistência e Listagem:** Após a submissão, o redirecionamento para a tela de listagem confirmou que o dado foi processado e renderizado corretamente na tabela de cursos.
3. **Fluxo de Navegação:** O botão de acesso ao cadastro no header mostrou-se funcional e visível.

---

### 4. Planejamento de Testes Futuros (Backlog de QA)

Para aprofundar a análise, recomenda-se a execução dos seguintes cenários técnicos:

| Categoria | Descrição do Teste | Objetivo Técnico |
| :--- | :--- | :--- |
| **Validação de Input** | Submissão de campos com espaços em branco ou nulos. | Validar o tratamento de exceção no Front-end/Back-end. |
| **Segurança (XSS)** | Inserção de tags `<script>` nos campos de texto. | Verificar se há sanitização de dados para evitar execução de código malicioso. |
| **Responsividade** | Teste em diferentes Viewports (Mobile/Tablet). | Garantir que o header e a tabela de cursos se adaptem sem perda de funcionalidade. |
| **Status Codes** | Inspeção via aba Network (F12). | Validar se as respostas de API seguem o padrão REST (ex: 201 para criação). |

# Documentação de Planeamento e Análise de Testes

## 1. Explicação do Raciocínio Durante a Análise

O meu raciocínio prioriza, num primeiro momento, a análise do front-end e da interface do utilizador (UI/UX). Esta abordagem inicial é estratégica, pois a usabilidade e a clareza visual são os primeiros pontos de contacto e de aprovação por parte dos utilizadores finais e stakeholders.

Após esta validação estática e visual, o meu foco volta-se para a recolha de critérios de aceitação e regras de negócio. Isto permite-me mapear o "caminho feliz" e construir um entendimento sólido do âmbito de atuação. Com esta base, executo os testes funcionais documentados no meu charter exploratório.

Por fim, aprofundo a análise funcional inspecionando a camada de rede e comunicação com a API. O objetivo é validar a integridade das requisições e respostas HTTP (GET, POST, PUT, DELETE), garantindo que o fluxo de dados entre o cliente e o servidor ocorra sem erros.

---

## 2. Decisões Tomadas para a Criação dos Testes

### 2.1. Foco e Âmbito Inicial
* **Priorização do Fluxo Principal:** O teste do CRUD será iniciado pela operação de Criação (CREATE) do Curso, por ser o fluxo fundamental do sistema.
* **Validação de Front-end:** A etapa inicial focará estritamente no comportamento do Front-end, garantindo a documentação imediata de todos os defeitos encontrados nesta camada.

### 2.2. Técnicas de Teste Aplicadas
* **Partição de Equivalência e Validação de Campos:** Os testes abrangerão a validação de campos obrigatórios e a inserção de valores específicos, com atenção especial aos campos de "Data" e "Nº de Vagas".
* **Critérios de Aceitação:** Serão validados inputs válidos e inválidos com base nos critérios de aceitação vigentes para cada campo.

### 2.3. Processo de Execução, Registo e Evidência
* **Estrutura de Trabalho:** O processo seguirá a ordem de criação dos cenários de teste, execução, captura de resultados e geração de evidências.
* **Documentação de Defeitos e Melhorias:** Todo o comportamento inesperado ou oportunidade de melhoria seguirá o padrão rigoroso de: Evidenciar, Relatar e Documentar. Os registos utilizarão uma estrutura padronizada de Bug Report.

### 2.4. Abordagem Exploratória Contínua
* **Testes Adicionais:** Para além do âmbito definido inicialmente, a execução não se limitará de forma rígida. Testes adicionais e não previstos no Charter Exploratório original serão conduzidos e documentados conforme a necessidade surgir durante a exploração contínua da aplicação.
