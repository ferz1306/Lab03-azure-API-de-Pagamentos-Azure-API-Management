# 🔐 API de Pagamentos Segura com Azure API Management e Microsoft Entra ID

## 📌 Descrição

Este projeto demonstra a construção e proteção de uma API de pagamentos utilizando serviços do Microsoft Azure, com foco em autenticação, autorização e gerenciamento de APIs em um cenário próximo ao ambiente corporativo.

A solução implementa um fluxo completo de segurança, incluindo:

* Autenticação via Microsoft Entra ID (Azure AD)
* Autorização baseada em App Roles
* Validação de token JWT no Azure API Management (APIM)
* Controle de acesso via Subscription Key
* Consumo da API autenticada utilizando Postman

---

## 🛠️ Tecnologias utilizadas

* Microsoft Azure
* Azure API Management (APIM)
* Microsoft Entra ID (Azure AD)
* OAuth 2.0 (Client Credentials Flow)
* JWT (JSON Web Token)
* Postman
* API REST
* JSON

---

## 🚀 O que foi implementado

* Criação e publicação de uma API de pagamentos no Azure App Service
* Exposição da API através do Azure API Management
* Configuração de App Registration da API no Microsoft Entra ID
* Definição de permissões:

  * OAuth Scope (`access_as_user`)
  * App Role (`Payment.Api.Access`)
* Criação de App Registration cliente para consumo da API
* Concessão de permissões com Admin Consent
* Geração de token JWT via OAuth 2.0 (`client_credentials`)
* Configuração de policy `validate-jwt` no APIM
* Restrição de acesso por Subscription Key
* Testes completos utilizando Postman

---

## 🏗️ Arquitetura da solução

```text
Cliente (Postman / App Cliente)
        ↓
Microsoft Entra ID (OAuth 2.0 / JWT)
        ↓
Azure API Management (Subscription Key + Validate JWT)
        ↓
Backend API (Pagamentos)
```

---

## 🔐 Fluxo de autenticação e autorização

1. O cliente solicita um token ao Microsoft Entra ID
2. O Azure AD retorna um JWT contendo a role autorizada
3. A requisição é enviada ao Azure API Management
4. O APIM valida:

   * Subscription Key
   * Token JWT
   * Audience (aud)
   * Role (roles)
5. Após validação, a requisição é encaminhada ao backend
6. O backend processa a requisição e retorna a resposta

---

## 📸 Evidências do projeto

### 1. Infraestrutura da solução no Azure

![Infraestrutura](./1.%20Infraestrutura%20da%20solução%20no%20Azure.png)

---

### 2. Permissões da API com Admin Consent (Granted)

![API Permissions](./2.%20API%20Permissions%20+%20Granted.png)

---

### 3. Política de validação JWT no APIM

![Policy APIM](./3.%20Policy%20do%20APIM.png)

---

### 4. App Registration da API

![App API](./4.%20App%20Registration%20da%20API.png)

---

### 5. Configuração de App Role

![App Role](./5.%20App%20Role.png)

---

### 6. App Registration do cliente

![App Cliente](./6.%20App%20Registration%20do%20cliente.png)

---

### 7. Expose an API (Scope)

![Expose API](./7.%20Expose%20an%20API.png)

---

### 8. Geração de token no Postman

![Token](./8.%20Postman%20gerando%20token.png)

---

### 9. Teste final da API com sucesso

![Sucesso](./9.%20Postman%20chamando%20a%20API%20com%20sucesso.png)

---

## ✅ Resultado final

### Requisição enviada:

```json
{
  "valor": 100
}
```

### Resposta da API:

```json
{
  "status": "sucesso",
  "valor": 100,
  "id": 173
}
```

---

## 💡 Principais conceitos aplicados

* API Security
* Identity and Access Management (IAM)
* OAuth 2.0 Client Credentials Flow
* App Registration
* App Roles
* JWT Validation
* API Gateway (APIM)
* Controle de acesso com Subscription Key
* Integração segura entre aplicações

---

## 📚 Aprendizados obtidos

Este projeto permitiu consolidar conhecimentos práticos sobre:

* Segurança de APIs em ambiente cloud
* Autenticação e autorização com Azure AD
* Validação de tokens JWT no APIM
* Comunicação segura entre aplicações
* Estruturação de APIs em um cenário semelhante ao ambiente corporativo

---

## 📌 Observações

* Informações sensíveis como secrets e tokens foram omitidas por segurança
* O projeto pode ser expandido com:

  * Versionamento de API
  * Rate limiting no APIM
  * Monitoramento e logs
  * Integração com CI/CD

---
