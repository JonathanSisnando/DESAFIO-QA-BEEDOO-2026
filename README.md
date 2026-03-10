
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

Decisões tomadas para criação dos testes

## Decisões Tomadas para a Criação dos Testes

**1. Foco e Escopo Inicial**
* **Priorização do Fluxo Principal:** O teste do CRUD será iniciado pela operação de Criação (CREATE) do Curso, por ser o fluxo fundamental do sistema.
* **Validação de Front-end:** A etapa inicial focará estritamente no comportamento do Front-end, garantindo a documentação imediata de todos os bugs encontrados nesta camada.

**2. Técnicas de Teste Aplicadas**
* **Partição de Equivalência e Validação de Campos:** Os testes abrangerão a validação de campos obrigatórios e a inserção de valores específicos, com atenção especial aos campos de "Data" e "Nº de Vagas".
* **Critérios de Aceitação:** Serão validados inputs válidos e inválidos com base nos critérios de aceitação vigentes para cada campo.

**3. Processo de Execução, Registro e Evidência**
* **Estrutura de Trabalho:** O processo seguirá a ordem de criação dos cenários de teste, execução, captura de resultados e geração de evidências.
* **Documentação de Bugs e Melhorias:** Todo comportamento inesperado ou oportunidade de melhoria seguirá o padrão rigoroso de: Evidenciar, Relatar e Documentar. Os registros utilizarão uma estrutura padronizada de Bug Report.

**4. Abordagem Exploratória Contínua**
* **Testes Adicionais:** Além do escopo definido inicialmente, a execução não se limitará de forma engessada. Testes adicionais e não previstos no Charter Exploratório original serão conduzidos e documentados conforme a necessidade surgir durante a exploração contínua da aplicação.


Explicação do seu raciocínio durante a análise


o meu raciocinio prioriza primeiramente em analisar o front end, em como ele está desenvolvido, pois é o que irá impressionar de primeira mão o stakeholders, pois um UI/UX limpo e bem claro, é o que primeiro tem que ser aprovado por quem irá usalo

Após realizar a analise estática do sistema, irei focar no caminho feliz, coletar os critérios de aceitação e regras de negócio para poder construir um entendimento do que é testado e assim aplicar os testes que estão mapeados no charter exploratório, para colhimento do Teste funcional, após isso, irei realizar testes não funcionais no sistema em busca de erros de requisição: Get, Post, read, del


