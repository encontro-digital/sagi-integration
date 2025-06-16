
# 📘 Envio de Ingressos - Encontro Digital

## 🕒 Frequência

- **Diariamente**, às **03:00 da manhã (GMT-3)**.
- São enviados **todos os ingressos criados, atualizados ou com check-in realizado no dia anterior** (período de 1 dia).

---

## 📨 Formato da Requisição

- **Método:** `POST`
- **Content-Type:** `application/json`

### Sobre os valores numéricos:

- **Todos os valores monetários são enviados como inteiros (integer)**, representando **centavos**.

### Valores possíveis para enums:

| Campo               | Valores possíveis |
|------------------- |------------------ |
| `payment_method_id` | `"Cartão de Crédito"`, `"Boleto"`, `"Pix"`, `"Cortesia"`, `"Gratuito"` |
| `payment_status_id` | `"Aguardando"`, `"Pago"`, `"Cancelado"`, `"Estornado"` |

---

## ✅ Exemplo de Payload

```json
{
  "event": "ingresso_export",
  "period": {
    "start_date": "2025-06-15",
    "end_date": "2025-06-15"
  },
  "data": [
    {
      "_id": "60d21b4667d0d8992e610c85",
      "project_id": "projeto123",
      "event_id": "evento456",
      "sale_hash": "abc123xyz",
      "ticket_hash": "ticket789",
      "client_id": "cli123",
      "payer_id": "pay456",
      "product_id": "prod123",
      "product_id_response": "Ingresso VIP",
      "payment_status_id": "Pago",
      "payment_method_id": "Pix",
      "transaction_status": "paid",
      "payment_gateway": "pagarme",
      "transaction_id": "trans789",
      "checkin": true,
      "checkin_date": "2025-06-15T18:00:00Z",
      "confirmated": true,
      "approved_at": "2025-06-15T10:00:00Z",
      "createdAt": "2025-06-15T09:30:00Z",
      "updatedAt": "2025-06-15T19:00:00Z",
      "seller_hash": "seller123",
      "fields_text": "Observações adicionais"
    }
  ]
}
```

---

## 📋 Campos Enviados

| Campo                 | Tipo        | Descrição |
|---------------------- |----------- |---------- |
| `_id`                | string      | ID único do ingresso |
| `project_id`         | string      | Identificador do projeto |
| `event_id`           | string      | Identificador do evento |
| `sale_hash`          | string      | Hash da venda associada |
| `ticket_hash`        | string      | Código único do ingresso |
| `client_id`          | string      | ID do participante (usuário final) |
| `payer_id`           | string      | ID do comprador (pagador) |
| `product_id`         | string      | ID do produto |
| `product_id_response`| object      | Nome do produto |
| `payment_status_id`  | string      | Status do pagamento |
| `payment_method_id`  | string      | Meio de pagamento |
| `transaction_status` | string      | Status da transação |
| `payment_gateway`    | string      | Gateway de pagamento |
| `transaction_id`     | string      | ID da transação |
| `checkin`            | boolean     | Indica se o participante fez check-in |
| `checkin_date`       | string (ISO DateTime) | Data/hora do check-in |
| `confirmated`        | boolean     | Indica se a participação foi confirmada |
| `approved_at`        | string (ISO DateTime) | Data/hora de aprovação da venda |
| `createdAt`          | string (ISO DateTime) | Data/hora de criação do ingresso |
| `updatedAt`          | string (ISO DateTime) | Data/hora da última atualização |
| `seller_hash`        | string      | Hash do vendedor |
| `fields_text`        | string      | Campos adicionais em formato texto |
| `fields`             | object      | Campos adicionais (JSON) |
| `quantity`           | integer     | Quantidade de ingressos na venda |
| `approved_at`        | string (ISO DateTime) | Data de aprovação |
| `cancelled_at`       | string (ISO DateTime) | Data de cancelamento (se houver) |
| `coupon`             | string      | Cupom de desconto usado |
| `payer_type`         | string      | Tipo de pagador |
| `courtesy_reference` | string      | Código de referência da cortesia |
| `cortesy_hash_id`    | string      | Hash da cortesia |
| `expireAt`           | string (ISO DateTime) | Data de vencimento do ingresso |
| `reserved`           | boolean     | Indica se o ingresso está reservado |
| `marketing_params`   | object      | Parâmetros de marketing |

---

## ✅ Exemplo de Resposta Esperada

```json
{
  "status": "received"
}
```

O endpoint do cliente deve responder com **HTTP 200 OK**.

---
