# Exercício 3 - Recomendações de Segurança em relação ao Log de Auditoria

Neste exercício você aprenderá sobre recomendações de segurança que ajudam a proteger suas contas contra riscos usando o log de auditoria.
O serviço SAP Audit Log é um serviço de plataforma que armazena todos os logs de auditoria gravados em seu nome por outros serviços de plataforma que você usa. Ele permite que você recupere os logs de auditoria da sua subconta por meio da [API de recuperação de log de auditoria](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-log-retrieval-api- uso para subcontas no ambiente cloud-foundry) ou visualizá-los usando o serviço SAP Audit Log Viewer. O tempo de retenção padrão é de 90 dias, após os quais os dados do log de auditoria são excluídos.
Por isso, recomendamos baixar logs de auditoria regularmente e salvá-los, de preferência em um sistema de log de auditoria central e existente ou em um sistema de gerenciamento de eventos e informações de segurança (SIEM) de sua escolha. Isso pode ser feito por meio da API de recuperação de log de auditoria ou no serviço SAP Audit Log Viewer.

# Recomendações de segurança relevantes
-BTP-AUD-0001


## Exercício 3.1 Assine o serviço SAP Audit Log Viewer

Neste exercício, você assinará o **Serviço Visualizador de Log de Auditoria**

1. Abra o **Cockpit SAP BTP**.

   <br><img src="/exercises/ex3/images/audit0.png" width="70%">

2. Navegue até sua **subconta de trilha** clicando no bloco. Acesse **Mercado de Serviços**.

  <br><img src="/exercises/ex3/images/audit02.png" width="70%">

3. Insira **auditoria** no campo de pesquisa. Selecione **Serviço Visualizador de Log de Auditoria** e clique nele.

<br><img src="/exercises/ex3/images/audit1.png" width="70%">
  
4. Agora assine. Isso é feito usando o botão **criar** no canto superior direito. O **Audit Log Mangement Service** pode ser usado posteriormente para configurar o período de retenção e recuperar os arquivos de log do seu sistema SIEM. Não precisamos disso neste exercício.

<br><img src="/exercises/ex3/images/audit2.png" width="70%">

5. Uma janela é exibida. Clique no botão **criar**.

<br><img src="/exercises/ex3/images/audit3.png" width="70%">

6. Navegue até **Ver assinatura**
   
<br><img src="/exercises/ex3/images/audit4.png" width="70%">

8. Em **Instâncias e Assinaturas** agora você pode ver o novo aplicativo **Audit Log Viewer Service** e o link para o aplicativo próximo a ele.
   
<br><img src="/exercises/ex3/images/audit5.png" width="70%">


## Exercício 3.2 Configurar o serviço SAP Audit Log Viewer

  Neste exercício, você configurará o serviço SAP Audit Log Viewer para ver entradas de log relevantes de auditoria.

1. Abra o **Cockpit SAP BTP**.

   <br><img src="/exercises/ex3/images/audit0.png" width="70%">

2. Vá para a **subconta da trilha** clicando no bloco

3. Escolha o item de menu **Segurança --> Coleções de funções** e clique no botão **"+"** para criar uma nova coleção de funções

<br><img src="/exercises/ex3/images/audit6.png" width="70%">

4. Na janela pop-up, insira o nome da coleção de funções **Audit Log Viewer**. Na descrição, insira **Ver os logs relevantes de auditoria no visualizador de log de auditoria**.
Clique no botão **Criar**.

<br><img src="/exercises/ex3/images/audit7.png" width="70%">

5. Agora você pode ver a coleção de funções **Visualizador de log de auditoria** junto com as outras coleções de funções. Clique em **">"** no lado direito da coleção de funções recém-criada para abrir os detalhes.

6. Na janela estendida você pode atribuir funções e usuários à coleção de funções. Comece a atribuir as duas funções do serviço visualizador de log de auditoria chamado **Auditlog_Auditor** à coleção de funções.
Para fazer isso, clique no botão **Editar**.

<br><img src="/exercises/ex3/images/audit8.png" width="70%">

8. No modo de edição, pesquise no nome da função as duas funções chamadas **Auditlog_Auditor**.

<br><img src="/exercises/ex3/images/audit9.png" width="70%">

9. Marque as duas funções chamadas **Auditlog_Auditor** e clique no botão "Adicionar".

<br><img src="/exercises/ex3/images/audit10.png" width="70%">

11. Vá para a seção **Usuários** e insira o endereço de e-mail do seu **usuário do SAP Cloud Identity Service**. Insira-o no campo **ID** e selecione a entrada na lista.

<br><img src="/exercises/ex3/images/audit12.png" width="70%">
 
12. Clique no botão **Salvar** para salvar suas alterações.

<br><img src="/exercises/ex3/images/audit13.png" width="70%">
 
13. O resultado será que o usuário com as autorizações atribuídas poderá usar o **serviço Audit Log Viewer**. Você precisa estar logado no cockpit com este usuário para poder ver o Viewer na próxima etapa.


## Exercício 3.3 Verifique os logs de auditoria e baixe as entradas do log de auditoria por meio do serviço SAP Audit Log Viewer

Você pode fazer download dos logs de auditoria por meio da API de recuperação de log de auditoria para importá-los para seu sistema de gerenciamento de informações e eventos de segurança (SIEM) ou pode baixá-los por meio da interface do usuário do Viewer para armazená-los como backup em seu sistema de arquivos.
Agora você aprende como baixá-los por meio da interface do usuário.

1. Abra o **Cockpit SAP BTP**.

   <br><img src="/exercises/ex3/images/audit0.png" width="70%">

2. Navegue até **Serviços > Instâncias e Assinaturas**. Em Assinaturas, você verá o **serviço Audit Log Viewer**. Ao lado do campo de texto há um link para a interface do usuário. Clique nisso.
 
   <br><img src="/exercises/ex3/images/audit14.png" width="70%">

4. Uma página de login aparecerá. Selecione seu locatário **Teste SAP Cloud Identity Service**.

5. Um pop-up solicitará **E-mail** e **Senha**. Insira o e-mail do seu usuário SAP Cloud Identity e sua senha.

    <br><img src="/exercises/ex1/images/logon_XSUAA_trial.png" width="50%">

6. Como habilitamos no primeiro exercício a autenticação multifator (MFA) usando senha única baseada em tempo (TOTP) para aplicativos em BTP, a janela **Autenticação de dois fatores** será exibida. Gere a senha no seu dispositivo móvel e insira-a. Depois de inserir a senha baseada em tempo gerada pelo seu dispositivo móvel, o aplicativo **Audit Log Viewer** será aberto.

   <br><img src="/exercises/ex1/images/MFASAPBUILDAPPSPasscode.png" width="70%">

3. Na **IU do Visualizador de log de auditoria** recém-aberta, você pode aceitar o período padrão ou selecionar um período específico para ver as entradas mais recentes do log de auditoria. No lado direito existe um botão para recuperar os logs após a seleção do prazo.

    <br><img src="/exercises/ex3/images/audit17.png" width="70%">

4. Agora você pode ver as entradas de log das alterações relevantes da auditoria específica, que foram realizadas recentemente.

    <br><img src="/exercises/ex3/images/audit18.png" width="70%">

5. O período de retenção dos logs no ambiente Cloud Foundry é de 90 dias. Portanto, é recomendável fazer backup dos arquivos de log de auditoria ou importá-los por meio da API de recuperação de log de auditoria para um sistema SIEM. Você pode baixar os arquivos da interface do usuário. Para fazer isso, clique no botão de download no meio do título.

    <br><img src="/exercises/ex3/images/audit19.png" width="70%">

6. Na janela pop-up, selecione um local em seu laptop para salvar o arquivo **viewLogs.json**. Clique em **Salvar**.

Agora você sabe fazer download dos arquivos de log relevantes de auditoria para backup.

## Resumo

Neste exercício, você configurou o **serviço SAP Audit Log Viewer** para ver as entradas de log relevantes de auditoria. Além disso, você viu como fazer download dos arquivos audit.log antes do término do período de retenção.
