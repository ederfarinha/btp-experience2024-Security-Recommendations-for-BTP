[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/teched2023-XP264)](https://api.reuse.software/info/github.com/SAP-samples/teched2023-XP264)

#XP264  - Get Hands-On Security Recommendations for Your SAP BTP Environment

## Descrição

Este repositório contém o material para a sessão do SAP BTP Experience Brazil 2024 chamada XP264 - Get Hands-On Security Recommendations for Your SAP BTP Environment.

## Visão geral

Nesta sessão os participantes aprenderão sobre as recomendações de segurança para serviços BTP e como implementá-las. As [Recomendações de segurança SAP BTP](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations) estão disponíveis no SAP Help Portal nas seções para a SAP Business Technology Platform. É uma lista com recomendações SAP para as configurações de serviços SAP BTP para ajudar os clientes a atingir suas metas de conformidade e proteger seus negócios.

## Requisitos

Os requisitos para seguir os exercícios neste repositório são contas de teste ativas para o SAP BTP e para o serviço SAP Cloud Identity.

**Primeiro você precisa obter sua conta de teste SAP BTP. Siga as instruções:**
[Obtenha uma conta gratuita na avaliação do SAP BTP](https://developers.sap.com/tutorials/hcp-create-trial-account.html)

**A segunda tarefa é ativar sua avaliação do SAP Cloud Identity Services. Siga as instruções neste blog:**
[SAP Cloud Identity Services oferecidos como versão de teste](https://blogs.sap.com/2023/04/13/sap-cloud-identity-services-offered-as-trial-version/)

💡Você deve ter acesso à sua caixa de correio, que usou ao se registrar em sua conta de teste BTP para ativar sua conta de teste do Cloud Identity Services.

**A terceira tarefa é instalar no seu dispositivo móvel um aplicativo de autenticação baseado em tempo (como SAP Authenticator, Google Authenticator ou Microsoft Authenticator).**


Agora você está pronto para iniciar os exercícios.

## Exercícios

- [Introdução](exercises/ex0/)
- [Exercício 1 - Habilitar autenticação multifator para aplicativos](exercises/ex1/)
     - [Exercício 1.1 - Configure SAP Build Apps e insira o aplicativo com o usuário do seu provedor de identidade de avaliação](exercises/ex1#exerc%C3%ADcio-11---configure-sap-build-apps-e-insira-o-aplicativo-com-o-usu%C3%A1rio-do-seu-provedor-de-identidade-de-teste)
     - [Exercício 1.2 - Configurar autenticação multifator para acessar aplicativos SAP Build](exercises/ex1#exercise-12---Configure-Multi-Factor-Authentication-to-access-SAP-Build-Apps)
     - [Exercício 1.3 - Habilitar MFA para seu usuário](exercises/ex1#exerc%C3%ADcio-13---habilite-mfa-para-seu-usu%C3%A1rio)
    
- [Exercício 2 - Recomendações de segurança em relação ao acesso e autenticação de usuários](exercises/ex2/)
     - [Exercício 2.1 - Gerenciar administradores obsoletos](exercises/ex2#exercise-21---Gerenciar administradores obsoletos)
     - [Exercício 2.2 - Definindo uma política de senha personalizada](exercises/ex2#exercise-22---Defining-a-custom-password-policy)
     - [Exercício 2.3 - Manter o acesso público aos aplicativos por auto-registro desabilitado](exercises/ex2#exercise-23---Keep-public-access-to-applications-by-self---registration-disabled)
     - [Exercício 2.4 - Manter o Social Sign-On desativado](exercises/ex2#exercise-24---Keep-Social-Sign---On-disabled)
- [Exercício 3 - Recomendações de segurança em relação ao log de auditoria](exercises/ex3/)
     - [Exercício 3.1 - Assine o serviço SAP Audit Log Viewer](exercises/ex3/README.md#Exercise-31---Subscribe-to-the-SAP-Audit-Log-Viewer-service)
     - [Exercício 3.2 - Configurar o serviço SAP Audit Log Viewer](exercises/ex3/README.md#Exercise-32---configure-the-sap-audit-log-viewer-service)
     - [Exercício 3.3 - Verifique os logs de auditoria e baixe as entradas do log de auditoria por meio do serviço SAP Audit Log Viewer](exercises/ex3/README.md#exercise-32---check-the-audit-logs-and-download-audit -log-entries-via-the-sap-audit-log-viewer-service)



**IMPORTANTE**

Seu repositório deve conter a pasta .reuse e LICENSES e a seção Licença abaixo. NÃO REMOVA a seção ou pastas/arquivos. Além disso, remova todos os ativos de modelo não utilizados (imagens, pastas, etc.) da pasta de exercícios.

## Contribuindo
Por favor, leia [CONTRIBUTING.md](./CONTRIBUTING.md) para entender as diretrizes de contribuição.

## Código de Conduta
Leia o [Código de conduta de código aberto da SAP](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## Como obter suporte

O suporte para o conteúdo deste repositório está disponível durante a sessão online para a qual este conteúdo foi projetado. Caso contrário, você pode solicitar suporte através da aba [Issues](../../issues).

## Licença
Copyright (c) 2024 SAP SE e LAB2DEV. Todos os direitos reservados. Este projeto está licenciado sob a Licença de Software Apache, versão 2.0, exceto quando indicado de outra forma no arquivo [LICENSE](LICENSES/Apache-2.0.txt).
