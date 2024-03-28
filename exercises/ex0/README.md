# Introdução

Depois de ativar sua conta de avaliação do SAP BTP com acesso ao BTP Cockpit e a avaliação do SAP Cloud Identity (SCI) com acesso ao console administrativo do SAP Cloud Identity, você estará pronto para as próximas etapas.

Esperamos que você tenha criado uma **subconta de avaliação** no cockpit da sua conta de avaliação SAP BTP.

Também esperamos que você tenha ativado o **Ambiente Cloud Foundry**.

Finalmente você instalou em seu dispositivo móvel um aplicativo de autenticação baseado em tempo (como SAP Authenticator, Google Authenticator ou Microsoft Authenticator).

Seguindo o blog para configurar o **teste do SAP Cloud Identity Services (SCI)** você já estabeleceu a configuração Trust em sua subconta de teste BTP, que adiciona o Provedor de identidade de teste para aplicativos para permitir que os usuários do seu Provedor de identidade de teste façam logon para aplicativos consumidos nesta subconta.

## Resultado da preparação

1. Faça logon no cockpit pessoal da sua conta de avaliação SAP BTP com o usuário que você usou para ativar a conta. Acesse a [**página de avaliação do SAP BTP**](https://account.hanatrial.ondemand.com/trial/#/home/trial) e clique em **Log On**.

2. Você verá um botão principal na tela de boas-vindas do SAP BTP Cockpit. Clique em **Ir para sua conta de teste** para navegar até sua conta global.
    **Marque** o link para acesso rápido e rápido ao **cockpit BTP**.

3. Navegue até a subconta e verifique se o tempo de execução do Cloud Foundry está ativado. Se **não** estiver ativado, clique em **Ativar Cloud Foundry**. Isso pode levar alguns segundos. Esta página exibe o estado atual da subconta. Você pode gerenciar suas assinaturas e acessar diferentes ambientes de execução. Também mostra informações fundamentais do ambiente Cloud Foundry, como o endpoint da API e os espaços disponíveis.

<br>![](/exercises/ex0/images/audit0.png)

<br>![](/exercises/ex0/images/Subaccount%20Overview.png)

4. Verifique a configuração de confiança para usuários do aplicativo

    Navegue no BTP Cockpit para **Trial HOME -> sua subconta inicial (por exemplo, Trial Subaccount 1 ) -> Security -> Trust Configuration**

    Verifique se o Provedor de Identidade Personalizado para aplicativos está configurado. Caso contrário, volte aos preparativos e siga o blog [SAP Cloud Identity Services oferecidos como versão de teste](https://community.sap.com/t5/technology-blogs-by-sap/sap-cloud-identity-services-offered-as-trial-version/ba-p/13552272) sobre como configurá-lo.

<br>![](/exercises/ex0/images/Subaccoount1_TrustConfiguration.png)

5. Faça logon em seu provedor de identidade pessoal - SCI Cockpit (SCI - serviço SAP Cloud Identity).

    Navegue em sua subconta até **Instâncias e assinaturas**. Clique no bloco ao lado do aplicativo inscrito **Cloud Identity Services** que diz **Ir para o aplicativo** quando você passa o mouse sobre ele. Uma nova janela é aberta com o Cockpit da conta de avaliação do SAP Cloud Identity Services. **Marque** o link para acesso rápido e rápido ao **SCI cockpit**.

     <br>![](/exercises/ex0/images/SubaccountInstanceandSubscriptions.png)
   
      <br>![](/exercises/ex0/images/SCICockpit.png)

7. No **console de administração SCI -> Aplicativos e Recursos -> Aplicativos** você verá a configuração de confiança que foi estabelecida pela sua conta de teste BTP. É denominado **XSUAA_trial**.

<br>![](/exercises/ex0/images/SCI_XSUAA_trial.png")

    Os aplicativos que você implanta em sua subconta BTP agora podem delegar a autenticação ao locatário SCI que você acabou de criar. E no **console de administração do SCI** você pode configurar as diversas opções de autenticação e autenticação multifator.

  8. Efetue logout no **console administrativo do SCI**.

<br><img src="/exercises/ex1/images/SCI_logout.png" width="70%">

## Resumo

Agora que você verificou todos os pré-requisitos e tem acesso aos dois cockpits administrativos, SAP BTP Cockpit e SCI Cockpit,
Continue para - [Exercício 1 - Habilitar autenticação multifator para aplicativos](../ex1/README.md)
