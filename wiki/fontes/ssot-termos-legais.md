---
tipo: fonte
arquivo: ingeridos/wecareu_termos_legais_lgpd_e_seguran_a.md
origem: extração via IA (Gemini), snapshot de 2026-10-20
criado: 2026-10-20
atualizado: 2026-10-20
---

# SSoT de termos, LGPD e segurança

Consolida o que os rascunhos jurídicos e o documento de segurança já diziam, com alguns acréscimos.

## Pontos principais

- Intermediação: sem responsabilidade pelo serviço físico. Zero comissão explícita nos termos. Idade 18+. Suspensão sem aviso.
- Coleta: identificação, agendamento, localização, dispositivo, pagamento tokenizado.
- Consentimento de imagem em 1 clique no checkout.
- Criptografia em trânsito e em repouso. Localização em tempo real só entre as partes e só durante o serviço.
- Jest e Maestro devem checar máscara de dados sensíveis e permissões (GPS, câmera, galeria) antes do deploy.
- Gateway com 3DS (exemplo: e-Rede). API com OAuth 2.0 / JWT. MFA só no `web-admin`.
- Shadowban como sinkhole: a ação parece ter dado certo e é descartada. Device fingerprint: vários Artistas no mesmo aparelho, fora de um business, vão para revisão manual.

Ver [[protecao-de-dados]], [[seguranca-do-atendimento]]. A localização em tempo real continua fora do MVP por [[decisoes-2026-10-20]].
