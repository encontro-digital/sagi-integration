
# 📘 Envio de Vendas - Encontro Digital

## 🕒 Frequência

- **Diariamente**, às **03:00 da manhã (GMT-3)**.
- São enviados **todos os pedidos de venda criados ou atualizados no dia anterior**.

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

## 📋 Campos Enviados

| Campo                 | Tipo        | Descrição |
|---------------------- |----------- |---------- |
| `_id`                | string      | ID único da venda |
| `project_id`         | string      | Identificador do projeto |
| `event_id`           | string      | Identificador do evento |
| `coupon`             | string      | Código de cupom de desconto (se houver) |
| `payer_type`         | string      | Tipo de pagador (cpf, cnpj) |
| `sale_hash`          | string      | Hash único da venda |
| `price`              | integer     | Valor da venda antes de descontos (em centavos) |
| `discount`           | integer     | Valor total de desconto aplicado (em centavos) |
| `installment`        | integer     | Número de parcelas |
| `installment_value`  | integer     | Valor de cada parcela (em centavos) |
| `total`              | integer     | Valor total da venda (em centavos) |
| `tax`                | integer     | Taxa da venda (em centavos) |
| `transaction_tax`    | integer     | Taxa de transação (em centavos) |
| `administration_tax` | integer     | Taxa administrativa (em centavos) |
| `fees`               | integer     | Juros (em centavos) |
| `net_total`          | integer     | Valor líquido da venda (em centavos) |
| `transaction_id`     | string      | ID da transação no gateway |
| `boleto_url`         | string      | URL para geração do boleto (se aplicável) |
| `boleto_barcode`     | string      | Código de barras do boleto |
| `transaction_status` | string      | Status da transação |
| `payment_gateway`    | string      | Meio de pagamento utilizado |
| `approved_at`        | string (ISO DateTime) | Data/hora de aprovação |
| `cancelled_at`       | string (ISO DateTime) | Data/hora de cancelamento |
| `createdAt`          | string (ISO DateTime) | Data/hora de criação da venda |
| `quantity`           | integer     | Quantidade de produtos/itens vendidos |
| `payment_method_id`  | string      | Método de pagamento |
| `payment_status_id`  | string      | Status de pagamento |
| `fields`             | object      | Campos adicionais personalizados |
| `fields_text`        | string      | Campos adicionais em formato texto |
| `product_id`         | string      | ID do produto |
| `product_id_response`| object       | Dados do produto |
| `client_id`          | string      | ID do cliente final |
| `payer_id`           | string      | ID do comprador |
| `cortesy_hash_id`    | string      | Hash da cortesia |
| `expireAt`           | string (ISO DateTime) | Data de vencimento |
| `seller_hash`        | string      | Hash do vendedor |
| `marketing_params`   | object      | Parâmetros de marketing associados à venda |

---

## ✅ Exemplo de Resposta Esperada

```json
{
  "status": "received"
}
```
