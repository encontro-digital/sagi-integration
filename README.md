# 📘 Documentação de Integração - Webhooks Encontro Digital

## 📡 Visão Geral

A plataforma **Encontro Digital** realiza **envios automáticos de dados para endpoints fornecidos pelo cliente**. Os envios ocorrem em horários programados, permitindo ao cliente receber e processar os dados de forma automatizada.

---

## 📅 Frequência de Envios

| Tipo de Dados               | Frequência                      | Horário (GMT-3) |
|---------------------------- |-------------------------------- |---------------- |
| Cadastros, Vendas e Ingressos | Diariamente                    | 03:00           |
| Conciliação Financeira       | Semanalmente (toda quinta-feira) | 03:00           |

---

## 📌 Considerações Gerais

- **Formato dos valores monetários:** Sempre enviados como **inteiros**, representando o valor **em centavos**.
- **Campos com enums padronizados:**

| Campo               | Valores possíveis                        |
|-------------------- |---------------------------------------- |
| `payment_method_id` | `"Cartão de Crédito"`, `"Boleto"`, `"Pix"`, `"Cortesia"`, `"Gratuito"` |
| `payment_status_id` | `"Aguardando"`, `"Pago"`, `"Cancelado"`, `"Estornado"` |
| `operation`         | `"Crédito"`, `"Saque"`, `"Estorno"` |

- **Content-Type de todas as requisições:** `application/json`
- **Resposta esperada em todos os endpoints:**

```json
{
  "status": "received"
}
```

---

## 📤 Envio de Cadastros

(Bloco detalhado de Cadastros conforme criado anteriormente, incluindo exemplo de payload, tabela de campos e observações sobre valores inteiros.)

---

## 📤 Envio de Vendas

(Bloco detalhado de Vendas com ajustes de centavos, enums e os campos da estrutura fornecida.)

---

## 📤 Envio de Ingressos

(Bloco detalhado de Ingressos, seguindo as regras de valores inteiros, enums e estrutura de campos informada.)

---

## 📤 Envio de Conciliação Financeira

(Bloco detalhado de Conciliação Financeira conforme gerado na última resposta, com todas as regras de valores, enums e campos descritos.)

---

## ✅ Considerações Finais

- Recomendamos que o cliente implemente validações para garantir a consistência dos dados recebidos.
- Mudanças futuras nos campos ou estrutura serão comunicadas previamente pela equipe técnica do **Encontro Digital**.
