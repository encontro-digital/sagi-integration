
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

- **Formato dos valores monetários:** Sempre enviados como **inteiros (integer)**, representando o valor **em centavos**.

- **Banco de dados:** A Encontro Digital utiliza um banco **NoSQL (MongoDB)**.  
  Portanto, o campo **`_id` não é numérico**. Caso o banco de destino do cliente seja SQL, recomenda-se **reservar um campo específico para armazenar o `_id` como string**.

- **Envio baseado em atualização (Cadastros, Vendas e Ingressos):**
  - Os dados desses endpoints são enviados com base no campo **`updatedAt`**.
  - O cliente deve validar:
    - **Se o `_id` já existe no banco de destino → realizar um update.**
    - **Se o `_id` não existir → realizar uma inserção.**

- **Enums padronizados:**

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

O endpoint do cliente deve sempre retornar **HTTP 200 OK**.

---

## 📂 Documentação por Endpoint

- [📄 Cadastros](cadastros.md)
- [📄 Vendas](vendas.md)
- [📄 Ingressos](ingressos.md)
- [📄 Conciliação Financeira](conciliacao.md)

---

## ✅ Considerações Finais

- Recomendamos que o cliente implemente validações para garantir a consistência dos dados recebidos.
- Mudanças futuras nos campos ou estrutura serão comunicadas previamente pela equipe técnica do **Encontro Digital**.
