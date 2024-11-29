
# Usando _Prompt Engineering_ em Testes de Software

Ao usar _prompt engineering_, é possível criar prompts precisos e específicos para auxiliar em diversas tarefas de teste de software. Abaixo, seguem diferentes técnicas em diferentes cenários, com exemplos práticos.

## 1. Escrevendo Testes de API

**Cenário**: Gerar testes para o endpoint `/customers` que suporta paginação e filtragem.

### Pré-Prompt: Atribuição de Papel e Configuração

- "Você é um engenheiro de software especializado em testes de API usando Cypress. Escreva testes bem estruturados para o seguinte endpoint."

### Prompt Principal

- "O endpoint `/customers` aceita os parâmetros `page`, `limit`, `size` e `industry`. Ele retorna dados paginados de clientes, incluindo `id`, `name` e `employees`. Escreva testes Cypress para:
  - Validar respostas bem-sucedidas.
  - Testar valores de limite para `page` e `limit`.
  - Testar filtragem por `size` e `industry`.
  - Tratar cenários de erro para parâmetros inválidos."

### Exemplo de Saída

```javascript
describe('Testes de API para o endpoint /customers', () => {
  it('deve retornar dados paginados de clientes para parâmetros válidos', () => {
    cy.request({
      method: 'GET',
      url: '/customers',
      qs: { page: 1, limit: 10 }
    }).then((response) => {
      expect(response.status).to.eq(200);
      expect(response.body.customers).to.have.length(10);
      expect(response.body.pageInfo).to.have.property('totalPages');
    });
  });

  it('deve retornar erro 400 para valor de página inválido', () => {
    cy.request({
      method: 'GET',
      url: '/customers',
      qs: { page: -1, limit: 10 },
      failOnStatusCode: false
    }).then((response) => {
      expect(response.status).to.eq(400);
      expect(response.body.error).to.eq('Número de página inválido');
    });
  });

  it('deve filtrar clientes por indústria', () => {
    cy.request({
      method: 'GET',
      url: '/customers',
      qs: { industry: 'technology' }
    }).then((response) => {
      expect(response.status).to.eq(200);
      expect(response.body.customers.every(c => c.industry === 'technology')).to.be.true;
    });
  });

  it('deve filtrar clientes por tamanho', () => {
    cy.request({
      method: 'GET',
      url: '/customers',
      qs: { size: 'small' }
    }).then((response) => {
      expect(response.status).to.eq(200);
      expect(response.body.customers.every(c => c.size === 'smalll')).to.be.true;
    });
  });
});

```

## 2. Escrevendo Testes de Interface Gráfica de Usuário (GUI)

**Cenário:** Testar um formulário de login com Cypress.

### Pré-Prompt: Papel e Restrições

- "Você é um especialista em testes de interfaces gráficas usando Cypress. Escreva testes para um formulário de login com os seguintes requisitos:
  - Validar login bem-sucedido.
  - Testar mensagens de erro para credenciais inválidas.
  - Garantir que o campo de senha esteja mascarado."

### Prompt Principal

- "O formulário inclui campos `email` e `password` e um botão `Login`. Após o login, o usuário deve ser redirecionado para `/dashboard`."

### Exemplo de Saída

```js
describe('Testes do Formulário de Login', () => {
  it('deve realizar login com credenciais válidas', () => {
    cy.visit('/login');
    cy.get('#email').type('testuser@example.com');
    cy.get('#password').type('securepassword');
    cy.get('button[type="submit"]').click();
    cy.url().should('include', '/dashboard');
  });

  it('deve exibir erro para credenciais inválidas', () => {
    cy.visit('/login');
    cy.get('#email').type('invalid@example.com');
    cy.get('#password').type('wrongpassword');
    cy.get('button[type="submit"]').click();
    cy.get('.error-message').should('contain', 'Email ou senha inválidos');
  });

  it('deve mascarar o campo de senha', () => {
    cy.visit('/login');
    cy.get('#password').invoke('attr', 'type').should('eq', 'password');
  });
});

```

## 3. Escrevendo Testes de Componentes React

**Cenário:** Testar um componente `Button` em diferentes estados.

### Pré-Prompt: Instrução Contextual

- "Você é um engenheiro de software escrevendo testes de componentes React com Jest e React Testing Library."

### Prompt Principal

- "Escreva testes para um componente `Button` com as props: `label`, `onClick` e `disabled`. Teste o seguinte:
  - Renderização com o rótulo correto.
  - Chamadas de `onClick` ao clicar.
  - Não chamar `onClick` quando `disabled`."

### Exemplo de Saída

```js
import { render, screen, fireEvent } from '@testing-library/react';
import Button from './Button';

describe('Testes do Componente Button', () => {
  it('renderiza com o rótulo correto', () => {
    render(<Button label="Enviar" onClick={() => {}} />);
    expect(screen.getByRole('button')).toHaveTextContent('Enviar');
  });

  it('chama onClick ao clicar', () => {
    const onClickMock = jest.fn();
    render(<Button label="Enviar" onClick={onClickMock} />);
    fireEvent.click(screen.getByRole('button'));
    expect(onClickMock).toHaveBeenCalledTimes(1);
  });

  it('não chama onClick quando desabilitado', () => {
    const onClickMock = jest.fn();
    render(<Button label="Enviar" onClick={onClickMock} disabled />);
    fireEvent.click(screen.getByRole('button'));
    expect(onClickMock).not.toHaveBeenCalled();
  });
});

```

## 4. Revisando Código de Testes

**Cenário:** Revisar um teste Cypress para manter boas práticas.

### Pré-Prompt

- "Você é um engenheiro de software especializado em revisar código de testes Cypress."

### Prompt Principal

- "Revise o seguinte código de teste Cypress para garantir boas práticas, legibilidade e manutenção. Sugira melhorias."

### Código de Exemplo

```js
cy.visit('/login');
cy.get('input').first().type('testuser@example.com');
cy.get('input').eq(1).type('password123');
cy.get('button').click();
cy.url().should('include', '/dashboard');

```

### Feedback de Exemplo

- **Sugestões de Melhoria:**
  - Use seletores específicos para inputs e botões para melhorar a legibilidade.
  - Encapsule ações reutilizáveis (ex.: login) em comandos personalizados.
  - Adicione comentários para facilitar a manutenção.

### Código Refatorado

```js
Cypress.Commands.add('login', (email, password) => {
  cy.get('#email').type(email);
  cy.get('#password').type(password);
  cy.get('button[type="submit"]').click();
});

// Uso:
cy.visit('/login');
cy.login('testuser@example.com', 'password123');
cy.url().should('include', '/dashboard');

```

## 5. Analisando Lacunas nos Testes Comparando com Requisitos

**Cenário:** Identificar casos de teste ausentes para uma página de produtos com base nos requisitos.

### Pré-Prompt

- "Você é um engenheiro de QA analisando lacunas na cobertura de testes. Compare os testes abaixo com os requisitos fornecidos."

### Prompt Principal

- "Requisitos para a página de `Produtos`:
  1. Exibir detalhes do produto (nome, preço, descrição).
  2. Permitir adicionar o produto ao carrinho.
  3. Lidar com produtos fora de estoque, desativando o botão 'Adicionar ao Carrinho' e exibindo uma mensagem.

Cobertura de Testes:

- Testes para exibir detalhes do produto.
- Testes para adicionar ao carrinho."

### Saída de Exemplo

- **Análise:**
  - **Testes existentes:**
    - Cobre exibição de detalhes do produto.
    - Cobre adicionar produtos ao carrinho.
  - **Testes ausentes:**
    - Não há testes para produtos fora de estoque.
    - Não há testes para verificar se o botão 'Adicionar ao Carrinho' está desativado quando fora de estoque.
    - Não há testes para a exibição da mensagem de fora de estoque.
- **Recomendações:**
  - Adicionar teste para verificar se o botão está desativado quando o produto está fora de estoque.
  - Adicionar teste para verificar a mensagem de fora de estoque.

___

[Voltar para o início](../README.md).
