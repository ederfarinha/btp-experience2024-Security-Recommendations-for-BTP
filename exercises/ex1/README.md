# Exercício 1 - Habilitar autenticação multifator para aplicativos

Neste exercício, mostraremos como habilitar a autenticação multifator (MFA) usando a senha única baseada em tempo (TOTP) para usuários do aplicativo. Em geral, recomendamos configurar métodos de autenticação baseada em risco, como autenticação multifator, para acesso ao **SAP BTP Cockpit** e ao **console administrativo SCI**. Na versão de teste isso não é possível, pois não há possibilidade de definir uma configuração confiável para sua conta BTP no nível de conta Global. Isso seria necessário para configurar a confiança para [usuários da plataforma](https://help.sap.com/docs/btp/best-practices/basic-platform-concepts).
A configuração no **console administrativo do SCI** é a mesma, apenas para um aplicativo diferente. Você usará **SAP Build Apps** como aplicativo para configurar a autenticação baseada em risco.

:bulb: **O que é autenticação multifator (MFA)?**

A autenticação multifator pode ser descrita como “Um mecanismo de autenticação que requer mais de um fator de autenticação distinto para uma autenticação bem-sucedida”.
Quando um usuário se autentica, ele deve fornecer credenciais válidas que consistem em um ou vários fatores. Ele usa vários fatores e informações para verificar a identidade do usuário. Muitos sistemas anteriores usam um fator, como nome de usuário/senha, também chamado de autenticação básica.
Agora, para fortalecer o processo de autenticação, usamos MFA que atua como mais uma camada de segurança para os usuários e reduz o risco de acesso não autorizado.

:bulb:**O que é senha de uso único baseada em tempo (TOTP)?**

Uma senha de uso único baseada em tempo (TOTP) é um código numérico gerado com um algoritmo padrão que usa a hora atual e uma chave como entrada. É fácil de usar e está disponível offline em um aplicativo gerador de escolha do usuário – geralmente em um dispositivo móvel. Aparece como números de seis dígitos que são regenerados a cada 30 segundos.


# Recomendações de segurança relevantes
-BTP-UAA-0001


## Exercício 1.1 - Configure SAP Build Apps e insira o aplicativo com o usuário do seu provedor de identidade de teste


1. Abra o **SAP BTP Cockpit** e navegue até sua conta global. Você deveria ter adicionado o URL aos favoritos no exercício **Primeiros passos**.

2. Navegue até **Boosters**

<br><img src="/exercises/ex1/images/GA-Boosters.png" width="70%">

4. Insira SAP Build Apps no campo de pesquisa. Clique em **Começar com SAP Build Apps**.

<br><img src="/exercises/ex1/images/gBoostergetstartedsapbuild apps.png" width="70%">

5. Agora um assistente é aberto e você segue o assistente e clica em próximo após cada entrada.

6. Verifique os pré-requisitos

<br><img src="/exercises/ex1/images/booster2.png" width="70%">

7. Selecione Cenário - selecione sua subconta

<br><img src="/exercises/ex1/images/booster3.png" width="70%">

8. Configure a subconta - insira sua subconta de teste

<br><img src="/exercises/ex1/images/Booster4.png" width="70%">

9. Adicionar usuários - insira seus endereços de e-mail para administradores e desenvolvedores

<br><img src="/exercises/ex1/images/Booster5.png" width="70%">

10. Revise suas entradas - Concluir

<br><img src="/exercises/ex1/images/booster6.png" width="70%">

11. Progredindo – isso demora um pouco

<br><img src="/exercises/ex1/images/Booster 7.png" width="70%">

12. **Sucesso** - Navegue até a subconta

<br><img src="/exercises/ex1/images/Boostersuccess.png" width="70%">

13. Vá para **Instâncias e assinaturas** em sua subconta. Clique no bloco para abrir **SAP Build Apps**

<br><img src="/exercises/ex1/images/openSAPBulidApps.png" width="70%">

14. Uma página de logon é aberta. Use seu **Provedor de identidade de conta de teste** para fazer login. É mostrado o provedor de identidade padrão (serviço SAP ID) e seu provedor de identidade de conta de trilha (SCI - SAP Cloud Identity).

<br><img src="/exercises/ex1/images/logonSAPBulidApp.png" width="70%">

15. Um pop-up solicitará **E-mail** e **Senha**. Insira o e-mail do seu usuário SAP Cloud Identity e sua senha.

<br><img src="/exercises/ex1/images/logon_XSUAA_trial.png" width="50%">

15. A autorização deve ser bem-sucedida, pois seu usuário é atribuído às coleções de funções necessárias durante o processo de criação do booster. Você verá a página de entrada do aplicativo **SAP Build App**.

<br><img src="/exercises/ex1/images/SAP Build App.png" width="70%">

16. **Saia** do SAP Build Apps e feche a janela do navegador.

<br><img src="/exercises/ex1/images/SAPBUILDsignout.png" width="70%">


## Exercício 1.2 - Configurar autenticação multifator para acessar aplicativos SAP Build

No exercício 1.1 habilitamos SAP Build Apps e os usuários configurados agora podem se autenticar com o provedor de identidade personalizado quando tentam acessar o aplicativo. Porém, queremos restringir o acesso à aplicação e permitir apenas o acesso com um segundo fator de autenticação.

1. Efetue logout da aplicação SAP Build e feche a janela do Navegador, caso ainda não tenha feito isso.

<br><img src="/exercises/ex1/images/Singoutsapbuild.png" width="70%">

2. Abra o **console administrativo do SCI**, no seu favorito ou no **BTP cockpit** (no BTP Cockpit, navegue até -> **Instâncias e assinaturas** -> clique no bloco ao lado de Nuvem Serviços de identidade).

<br><img src="/exercises/ex1/images/openSCItenant.png" width="70%">

3. Na janela pop-up, faça login com seu e-mail e senha no **console administrativo do SCI**.
   
<br><img src="/exercises/ex1/images/SigninSCITRIAL.png" width="70%">

4. No **console administrativo do SCI** navegue até **Aplicativos e Recursos -> Aplicativos**

<br><img src="/exercises/ex1/images/SCItenantApplications.png" width="70%">

5. No lado esquerdo você vê Pacotes de Aplicativos e Aplicativos de Sistema. Em Pacotes de Aplicativos, vemos o Aplicativo **XSUAA_trial**. Clique nele para ver os dados de configuração desta aplicação.

💡 **XSUAA** é um corretor de serviços para o servidor de autorização OAuth fornecido pelo Cloud Foundry UAA. Ele oferece serviços de autenticação e autorização para aplicativos de estilo microsserviço. Ele é usado por quase todos os aplicativos executados em SAP BTP no ambiente Cloud Foundry. Quando configurarmos a autenticação de dois fatores para este aplicativo, todos os aplicativos executados em SAP BTP no ambiente Cloud Foundry terão que fornecer um segundo fator para autenticação.
   
6. Na tela de configuração do aplicativo XSUAA_trial navegue até **Autenticação e Acesso**
   
<br><img src="/exercises/ex1/images/SCItrailXSUAA_AuAcc.png" width="70%">

7. Agora você pode ver a linha onde **Autenticação baseada em risco** pode ser configurada. Clique na pequena seta à direita.

<br><img src="/exercises/ex1/images/XSUAA_trial_app_SCI.png" width="70%">

8. No quadro **Autenticação Baseada em Risco** você tem a possibilidade de criar Regras de Autenticação e pode ver a Regra de Autenticação Padrão, que é **Permitir**.

  <br><img src="/exercises/ex1/images/SCI_XSUAA_trial_RBA_default.png" width="70%">

9. Altere a regra de autenticação padrão para **Ação padrão = autenticação de dois fatores** e **Método de dois fatores = TOTP**. Não esqueça de **salvar** no canto superior direito da página a nova configuração. Agora, o acesso a todos os aplicativos em sua subconta SAP BTP que usam o XSUAAA para autenticação exigem uma senha de uso único baseada em tempo (TOTP) como segundo fator.

<br><img src="/exercises/ex1/images/SCI_XSUAA_trial_RBA_MFA.png" width="70%">

Assim que a configuração for concluída, o sistema solicitará que o usuário selecione qualquer uma das opções disponíveis após o nome de usuário e a senha iniciais serem fornecidos. A próxima etapa é permitir que os usuários usem MFA.


## Exercício 1.3 - Habilite MFA para seu usuário

1. Navegue até a página de perfil de seus usuários no **SAP Cloud Identity**.

2. O perfil do usuário mostra os métodos de autenticação configurados para um usuário. Você pode acessá-lo através do seguinte link no ambiente de teste:

**https://"trialtenant-ID".trial-accounts.ondemand.com/ui/protected/profilemanagement**

Adicione **ui/protected/profilemanagement** em seu navegador após **https://"trialtenant-ID".trial-accounts.ondemand.com/**

Aqui você pode adicionar/remover seu método de autenticação, como acessar usando sua impressão digital, etc. As próximas etapas precisam de um dispositivo com um aplicativo de autenticação baseado em tempo instalado (como SAP Authenticator, Google Authenticator ou Microsoft Authenticator).

3. Abra a autenticação multifator. Clique em **Ativar autenticação de dois fatores TOTP**.

<br><img src="/exercises/ex1/images/userprofile1.png" width="70%">

4. Digitalize o código QR usando o aplicativo autenticador do seu dispositivo ou insira a chave manualmente. Depois de digitalizar ou inserir a chave, digite abaixo a senha gerada pelo aplicativo autenticador no seu dispositivo e clique em **Ativar**.

<br><img src="/exercises/ex1/images/userprofile2.png" width="70%">

5. Agora você tem um dispositivo configurado para autenticação TOTP de dois fatores

<br><img src="/exercises/ex1/images/userprofile3.png" width="70%">

6. Para voltar ao **console administrativo do SCI**, adicione **admin** em seu navegador após **https://"trialtenant-ID".trial-accounts.ondemand.com/** ou use seu favorito .

7. Efetue logout no **console administrativo do SCI**.

<br><img src="/exercises/ex1/images/SCI_logout.png" width="70%">

8. Navegue até **Cockpit SAP BTP -> Instância e assinaturas -> SAP Build Apps -> Abra o aplicativo**

<br><img src="/exercises/ex1/images/MFASAPBUILDAPPSOpen.png" width="70%">

8. Selecione nosso locatário SCI para fazer logon

<br><img src="/exercises/ex1/images/MFASAPBUILDAPPSLogon1.png" width="70%">

9. Um pop-up solicitará **E-mail** e **Senha**. Insira o e-mail do seu usuário SAP Cloud Identity e sua senha.

<br><img src="/exercises/ex1/images/logon_XSUAA_trial.png" width="50%">

9. O próximo pop-up solicitará uma **senha**. Abra o **aplicativo autenticador** que você está usando em nosso dispositivo móvel. Para continuar, insira a senha baseada em tempo gerada pelo seu dispositivo móvel para o aplicativo. Então continue.

<br><img src="/exercises/ex1/images/MFASAPBUILDAPPSPasscode.png" width="70%">

10. **Sucesso!** O aplicativo SAP Build é aberto.

<br><img src="/exercises/ex1/images/SAP Build App.png" width="70%">


## Resumo

Neste exercício você aprendeu como configurar o SAP Build e como habilitar a autenticação multifator (MFA) usando uma senha de uso único baseada em tempo (TOTP).



Continue para - [Exercício 2 - Recomendações de segurança em relação ao acesso e autenticação do usuário](../ex2/README.md)
