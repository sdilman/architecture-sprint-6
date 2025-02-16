# Схема GraphQL эквивалентная Swagger-контракту.

```
type Query {
  client(id: ID!): Client
  clientDocuments(id: ID!): [Document!]!
  clientRelatives(id: ID!): [Relative!]!
}

type Client {
  id: ID!
  name: String!
  age: Int
  documents: [Document!]
  relatives: [Relative!]
}

type Document {
  id: ID!
  type: String!
  number: String!
  issueDate: String
  expiryDate: String
}

type Relative {
  id: ID!
  relationType: String!
  name: String!
  age: Int
}
```

# Получить клиента по ID:

```
type Query {
  client(id: ID!): Client
}
```

# Получить список всех клиентов:

```
type Query {
  clients: [Client!]!
}
```

# Получить документы клиента по его ID:

```
type Query {
  clientDocuments(clientId: ID!): [Document!]!
}
```

# Получить родственников клиента по его ID:

```
type Query {
  clientRelatives(clientId: ID!): [Relative!]!
}
```