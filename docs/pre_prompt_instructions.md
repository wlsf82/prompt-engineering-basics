
# Instruções Pré-Prompt em _Prompt Engineering_

**Instruções pré-prompt** são um conceito essencial em _prompt engineering_. Pré-prompting refere-se a fornecer instruções preliminares ou contexto para moldar o entendimento e o comportamento da IA antes da tarefa ou consulta principal. Essa técnica ajuda a preparar o terreno para saídas mais relevantes e precisas.

## Por que usar instruções pré-prompt?

1. **Definir o Papel**: Especificar o "personagem" ou especialização da IA para influenciar o tom e o estilo.
2. **Fornecer Contexto**: Estabelecer informações prévias para a tarefa principal.
3. **Controlar a Saída**: Guiar como a resposta deve ser estruturada, formatada ou limitada.
4. **Gerenciar Tarefas Complexas**: Dividir tarefas em etapas gerenciáveis, começando com instruções preparatórias.

## Como as Instruções Pré-Prompt Funcionam

Instruções pré-prompt geralmente adicionam um texto introdutório ou de preparação antes da consulta principal. Elas podem assumir várias formas:

### 1. **Atribuição de Papéis**

Instruir a IA a assumir um papel específico para enquadrar a resposta em um contexto relevante.

- **Exemplo**: "Você é um engenheiro de software especializado em segurança cibernética. Explique como proteger um aplicativo web contra ataques de injeção de SQL."

### 2. **Diretivas Comportamentais**

Dizer à IA como se comportar ou estruturar a resposta.

- **Exemplo**: "Responda em um tom profissional e forneça referências quando aplicável."

### 3. **Provisão de Contexto**

Fornecer informações prévias necessárias antes de fazer a pergunta principal.

- **Exemplo**:
  - Pré-prompt: "O texto a seguir é de um artigo médico que discute os efeitos do exercício na saúde mental."
  - Consulta principal: "Resuma os principais achados em termos simples para um público geral."

### 4. **Restrições de Saída**

Especificar o formato, comprimento ou estrutura da resposta.

- **Exemplo**: "Forneça uma explicação de 3 parágrafos com uma introdução, corpo principal e conclusão."

## Quando usar Instruções Pré-Prompt

1. **Para Saídas Estruturadas**

- **Pré-prompt:** "Escreva no formato de uma lista numerada."
- **Consulta principal:** "Liste os cinco principais benefícios de aprender programação."

2. **Para Tópicos Complexos**

- **Pré-prompt:** "Explique este tópico como se estivesse ensinando a um iniciante"
- **Consulta principal:** "O que é computação quântica?"

3. **Para Melhorar a Criatividade**

- **Pré-prompt:** "Imagine que você é um poeta na França do século 19."
- **Consulta principal:** "Escreva um poema sobre a beleza da natureza."

4. **Para Consultas de Múltiplas Etapas**

- **Pré-prompt:** "Primeiro, analise o problema; depois, sugira uma solução."
- **Consulta principal:** "Quais são os desafios do trabalho remoto?"

## Dicas para Instruções Pré-Prompt Eficazes

1. **Seja Explícito:** Declare claramente o papel, tom ou estrutura desejados.

- Ruim: "Fale sobre IA."
- Bom: "Aja como um especialista em IA e discuta os benefícios da IA na educação."

2. **Use Delimitadores:** Indique onde termina a instrução pré-prompt e começa a tarefa principal (se necessário).

- Exemplo: "Contexto: Você é um historiador especializado no Renascimento. Tarefa: Explique o impacto da imprensa na educação."

3. **Itere:** Experimente diferentes pré-prompts para refinar os resultados.

- Exemplo 1: "Você é um palestrante motivacional."
- Exemplo 2: "Você é um palestrante motivacional falando para estudantes do ensino médio."

4. **Combine Instruções Pré-Prompt com as Principais:** Integre o papel e a tarefa de forma fluida.

- Exemplo: "Você é um nutricionista. Proponha um plano de refeições de 7 dias para alguém que segue uma dieta vegetariana."

## Exemplos na Prática

### Sem Instruções Pré-Prompt

- Prompt: "O que é aprendizado de máquina?"
  - Resposta: Uma definição genérica.

### Com Instruções Pré-Prompt

- Pré-prompt: "Você é um instrutor de IA ensinando uma turma de estudantes do ensino médio."
- Consulta principal: "Explique o que é aprendizado de máquina."
  - Resposta: Uma explicação simplificada adaptada para um público mais jovem.

## Casos de Uso

1. **Chatbots de Suporte ao Cliente**

- Pré-prompt: "Você é um agente de suporte simpático."
- Consulta principal: "Ajude um cliente a solucionar problemas de login."

2. **Geração de Código:**

- Pré-prompt: "Você é um especialista em JavaScript."
- Consulta principal: "Escreva uma função para calcular o fatorial de um número."

3. **Educação e Treinamento:**

- Pré-prompt: "Você é um professor de matemática explicando álgebra para alunos do 8º ano."
- Consulta principal: "Explique como resolver equações quadráticas."

## Principais Benefícios de Instruções Pré-Prompt

- Alinha a resposta da IA às expectativas do usuário.
- Garante um tom, estilo e relevância consistentes.
- Ajuda a gerenciar tarefas complexas ou de várias etapas.

As instruções pré-prompt são uma ferramenta valiosa em _prompt engineering_ para orientar o comportamento da IA e melhorar a qualidade da saída.

___

**Proximma seção:** [Usando _Prompt Engineering_ em Testes de Software](./using_prompt_engineering_in_software_testing.md).
