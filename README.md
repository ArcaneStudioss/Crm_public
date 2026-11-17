# Arcane CRM

CRM B2B multi-tenant, feito em **Node.js puro, sem dependências**, com SQLite embutido.

> Estudo de caso. O código-fonte é privado.

## Ideia central
Cada empresa cliente tem **um arquivo de banco só dela**. Um banco separado guarda apenas identidade e cobrança. Isso isola os dados por construção, simplifica backup e restauração por cliente e elimina uma classe inteira de vazamento entre empresas.

## O que faz
- **Modelos por nicho:** barbearia, imobiliária, loja, clínica, restaurante, academia e outros. Cada um traz nomenclatura, funil, automações e mensagens de WhatsApp prontas.
- **Chamar de volta:** aprende o ritmo de compra de cada cliente e avisa quando é hora de reativar.
- **Prospecção de leads** com OpenStreetMap e Google Places, com nota de 0 a 100 para a chance de o negócio precisar de um site.
- **Assinaturas com Stripe**, 2FA, login com Google, recuperação de senha e marca do cliente no painel.

## Decisões técnicas
- **Backup diário consistente** (`VACUUM INTO`), com verificação de integridade, cifrado (AES-256-GCM), retenção 7/4/6 e envio opcional para armazenamento S3 compatível. Teste automático faz backup, restaura e compara.
- **Deploy sem queda:** testes rodam antes de publicar, uma réplica sobe ao lado, e só então a principal é trocada. Migrações aditivas.
- Suíte de testes cobrindo isolamento entre empresas, segurança e cobrança.

## Stack
Node.js 22 · SQLite (`node:sqlite`) · Docker · Stripe

## Autor
Gabriel · [GitHub](https://github.com/ArcaneStudioss)
