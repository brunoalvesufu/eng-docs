Testes são uma parte crucial do desenvolvimento de software, ajudando a garantir que o código funcione conforme esperado e facilitando a manutenção. Vamos explorar como implementar testes em Node.js usando Jest, um popular framework de teste.

Primeiro, instale o Jest:

```bash
npm install --save-dev jest

```

1. Testes Unitários:

Testes unitários focam em partes isoladas do código, geralmente funções individuais.

Exemplo de uma função e seu teste unitário:

```javascript
// math.js
function sum(a, b) {
  return a + b;
}

module.exports = { sum };

// math.test.js
const { sum } = require('./math');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});

```

1. Testes de Integração:

Testes de integração verificam como diferentes partes do sistema trabalham juntas.

Exemplo de teste de integração para uma API Express:

```javascript
// app.js
const express = require('express');
const app = express();

app.get('/api/users', (req, res) => {
  res.json([{ id: 1, name: 'John' }, { id: 2, name: 'Jane' }]);
});

module.exports = app;

// app.test.js
const request = require('supertest');
const app = require('./app');

describe('GET /api/users', () => {
  it('responds with json containing a list of users', async () => {
    const response = await request(app)
      .get('/api/users')
      .expect('Content-Type', /json/)
      .expect(200);

    expect(response.body).toHaveLength(2);
    expect(response.body[0]).toHaveProperty('id');
    expect(response.body[0]).toHaveProperty('name');
  });
});
```

1. Mocking:

Mocking é útil quando você quer isolar a unidade que está sendo testada.

```javascript
// user.js
const axios = require('axios');

async function getUser(id) {
  const response = await axios.get(`https://api.example.com/users/${id}`);
  return response.data;
}

module.exports = { getUser };

// user.test.js
jest.mock('axios');
const axios = require('axios');
const { getUser } = require('./user');

test('should fetch user data', async () => {
  const user = { id: 1, name: 'John' };
  axios.get.mockResolvedValue({ data: user });

  await expect(getUser(1)).resolves.toEqual(user);
});
```

1. Cobertura de Testes:

Jest inclui uma ferramenta de cobertura de código. Adicione isto ao seu package.json:

```json
"scripts": {
  "test": "jest",
  "test:coverage": "jest --coverage"
}
```

1. Testes Assíncronos:

Jest tem suporte embutido para testes assíncronos:

```javascript
test('async test', async () => {
  const data = await fetchData();
  expect(data).toBe('peanut butter');
});
```

1. Setup e Teardown:

Use `beforeEach`, `afterEach`, `beforeAll`, e `afterAll` para configurar e limpar entre testes:

```javascript
beforeAll(() => {
  // Configuração antes de todos os testes
});

afterEach(() => {
  // Limpeza após cada teste
});
```

1. Snapshot Testing:

Útil para UI ou dados que não mudam frequentemente:

```jsx
it('renders correctly', () => {
  const tree = renderer
    .create(<Link page="<https://example.com>">Example</Link>)
    .toJSON();
  expect(tree).toMatchSnapshot();
});
```

1. Testes de Performance:

Você pode usar ferramentas como `loadtest` ou `artillery` para testes de carga.

```bash
npm install -g loadtest
loadtest -n 1000 -c 100 <http://localhost:3000/api/users>
```
