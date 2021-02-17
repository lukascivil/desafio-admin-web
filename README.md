**Desafio Admin-web**

Que tal ser desafiado pela Stone?

O seu desafio será construir uma aplicação de gestão financeira para o mundo dos negócios de uma nova empresa que está em constante crescimento.

Essa empresa terá você como desenvolvedor responsável pelas novas funcionalidades que a mesma deverá soltar no mercado. A empresa tem usuários em sua base de dados e agora vai começar a oferecer cartão de pagamento para eles. A empresa conta com times que fazem análise do usuário para a liberação do cartão de pagamento, mas o sistema ainda não existe, os mesmos usam uma planilha para controle interno. Essa planilha é alimentada por APIS existentes dentro da empresa.

Precisamos que a nossa aplicação de gestão seja capaz de fornecer aos nossos analistas as informações necessárias sobre os usuários da base e as solicitações de cartão. O mesmo deverá ser capaz de aprovar ou rejeitar os pedidos de cartão.

Os analistas trabalham em 2 times diferentes, para isso a API disponibiliza os roles de acesso para cada analista cadastrado, dessa forma será possível exibir somente informações relevantes para cada time e manter a segurança da informação.

Lembre-se que o time de back-end já criou a API que fornecerá as informações necessárias, entretanto, a estrutura entregue pela api pode ser alterada por você na aplicação Front de acordo com as necessidades.

O Analista deve ser capaz de:

- Aprovar ou rejeitar um pedido de cartão
- Atualizar o nome do usuário de um pedido de cartão
- Criar novo pedido de Cartão
- Visualizar Usuários da base
- Visualizar Cartões da base

Condições empregadas

- Analistas com role n1 não podem rejeitar um pedido de cartão e nem visualizar o salário base do Cliente

### **Estrutura de dados**

- **Users**

```json
{
  "name": "Nome do usuário",
  "email": "Email do usuário",
  "BirthDate": "Data de Nascimento do usuário",
  "createdAt": "Data de criação do usuário",
  "updatedAt": "Data da última atualização do usuário",
  "enabledFeatures": "Lista de recursos habilitados",
  "document": "Documento do usuário",
  "metadatas": {
    "validDocument": "O documento é válido?",
    "verified": "O usuário foi validado pela API?"
  },
  "address": "Endereço",
  "salaryBase": "Salário em centavos",
  "id": "Identificador único do usuário"
}
```

- **Analysts**

```json
{
  "id": "Id do analista",
  "user_id": "Id do usuário",
  "roles": "Cada role representa um grupo de acesso"
}
```

- **Cards**

```json
{
  "createdAt": "Data de criação do cartao",
  "updatedAt": "Data de atualização do cartão",
  "status": "Status do cartão",
  "id": "Id do cartão",
  "user_id": "Id do usuário",
  "metadatas": {
    "name": "Nome impresso no cartão usuário",
    "digits": "Dígitos do cartão"
  }
}
```

- **Features**

```json
{
  "result": [
    {
      "id": "id da feature",
      "name": "Nome da feature disponibilizada pela empresa"
    }
  ],
  "status": 200
}
```

Como rodar o Servidor

```sh
yarn
yarn start

ou

npm install
npm run start
```

output:

```
  http://localhost:3000/users
  http://localhost:3000/analysts
  http://localhost:3000/cards
  http://localhost:3000/features
```

Sua aplicacao deve contemplar todos os resources listados acima e realizar as seguintes chamadas para atender as nesessidades do analista.
Entretanto, caso seja necessário realizar qualquer outra chamada, fique a vontade.

- Users
  GET http://localhost:3000/users
  GET http://localhost:3000/users/:id

- Analysts
  GET http://localhost:3000/analysts

- Cards
  GET http://localhost:3000/cards
  PUT http://localhost:3000/cards/:id
  DELETE http://localhost:3000/cards/:id

- Features
  GET http://localhost:3000/features

Observações

- Cada cartão tem seu próprio estado e sempre parte do estado &quot;Solicitado&quot;. Um cartão pode ser solicitado pelo usuário ou pelo próprio analista. A responsabilidade do analista ao analisar um cartão é, &quot;aprovar&quot; ou &quot;rejeitar&quot;. E a responsabilidade da API será a de processar ou cancelar, parte que não precisaremos nos preocupar.

  - Requested -\&gt; Approved -\&gt; Processed
  - Requested -\&gt; Rejected -\&gt; Canceled

- Uma feature habilitada - que é retornada dentro de usuário - diz ao operador quais recursos aquele usuário tem disponível.
- A API também disponibiliza uma endpoint para um &quot;de para&quot; entre as features habilitadas para um usuário.

### **Layout**

Fique à vontade para definir seu próprio layout. Mas vamos deixar algumas dicas:

- O layout precisa "escalar", ou seja, qual a visão de futuro para o mesmo caso precise adicionar mais informações? Será necessário um re-layout ou o mesmo comportará?

### **Entrega**

- O código possui algum controle de dependências?
- O resultado final está completo para ser executado?
- O resultado final atende ao que se propõe fazer?
- O resultado final atende totalmente aos requisitos propostos?
- O resultado final é visualmente elegante?

### **Boas Práticas**

- O código está de acordo com o guia de estilo da linguagem?
- O código está bem estruturado?
- O código faz bom uso de _Design Patterns_?
- A separacao dos componentes visam atender o modelo implementado?

### **Documentação**

- O código foi entregue com um arquivo de README claro de como se guiar?
- O código possui comentários pertinentes?
- O código está em algum controle de versão?
- Os commits são pequenos e consistentes?
- As mensagens de commit são claras?

### **Deploy**

- Publique sua aplicação ([now](https://zeit.co/)/[heroku](https://www.heroku.com/)/[netlify](https://www.netlify.com/)/outros)
- Publique seu código no seu perfil no GitHub

### **Outras informações**

- Utilize React + Typescript
- Ferramentas como BootStrap, Material Ui, MaterializeCSS podem ser utilizadas
- Testes são legais, mas não são obrigatórios

### **Material de Estudo**

- [Boas Práticas de commit](https://github.com/stone-payments/stoneco-best-practices/blob/master/gitStyleGuide/README_pt.md)
- [Airbnb Javascript](https://github.com/airbnb/javascript)
- [The TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
