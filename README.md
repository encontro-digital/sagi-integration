# 📘 Integração Webhook - Encontro Digital

## 📡 Visão Geral

Este repositório contém a **documentação oficial** da integração via **Webhooks** da plataforma **Encontro Digital**.

Através desta integração, o cliente poderá receber, de forma automática, os dados de:

- ✅ Cadastros de participantes
- ✅ Vendas realizadas
- ✅ Ingressos emitidos
- ✅ Conciliação Financeira semanal

---

## 📅 Frequência de Envio

| Tipo de Dados               | Frequência                      | Horário (GMT-3) |
|---------------------------- |-------------------------------- |---------------- |
| Cadastros, Vendas e Ingressos | Diariamente                    | 03:00           |
| Conciliação Financeira       | Semanalmente (toda quinta-feira) | 03:00           |

---

## 📂 Estrutura do Repositório

| Documento                        | Conteúdo                         |
|-------------------------------- |-------------------------------- |
| [`documentacao_geral.md`](documentacao_geral.md) | Visão geral da integração |
| [`cadastros.md`](cadastros.md) | Detalhamento técnico do endpoint de Cadastros |
| [`vendas.md`](vendas.md) | Detalhamento técnico do endpoint de Vendas |
| [`ingressos.md`](ingressos.md) | Detalhamento técnico do endpoint de Ingressos |
| [`conciliacao.md`](conciliacao.md) | Detalhamento técnico do endpoint de Conciliação Financeira |

---

## 🛠️ Formato das Requisições

- **Método HTTP:** `POST`
- **Content-Type:** `application/json`
- **Formato de valores monetários:** Sempre **inteiros**, representando **centavos**.

---

## 🗃️ Observações sobre o Banco de Dados

A Encontro Digital utiliza um banco de dados **NoSQL (MongoDB)**.

- O campo `_id` é uma **string única do MongoDB** e **não é numérico**.
- Caso o banco de destino do cliente seja SQL, recomendamos **reservar um campo específico para armazenar o `_id` como texto**.

---

## 🕒 Controle de Atualizações

Para os endpoints de **Cadastros**, **Vendas** e **Ingressos**:

- Os dados são enviados com base no campo **`updatedAt`**.
- O cliente deve implementar lógica para verificar se o registro recebido já existe (**atualização**) ou se é um novo registro (**inserção**).

---

## ✅ Resposta Esperada dos Endpoints

```json
{
  "status": "received"
}
```

O endpoint do cliente deve sempre retornar **HTTP 200 OK** para confirmar o recebimento.

---

## 📞 Suporte

Dúvidas ou necessidade de suporte técnico?  
Entre em contato com a equipe de TI da **Encontro Digital**.
