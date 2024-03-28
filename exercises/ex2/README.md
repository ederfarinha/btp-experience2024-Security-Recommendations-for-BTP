# Exercício 2 - Recomendações de segurança em relação ao acesso e autenticação de usuários

Neste exercício você aprenderá mais recomendações de segurança que ajudam a proteger suas contas contra riscos relacionados ao acesso e autenticação

# Recomendações de segurança relevantes
-BTP-IAS-0002
-BTP-IAS-0003
-BTP-IAS-0005
-BTP-IAS-0017


## Exercício 2.1 Gerenciar administradores obsoletos

Faz sentido revisar regularmente se os usuários realmente precisam de acesso a tarefas administrativas e cockpits. Afinal, uma conta abandonada com altos privilégios pode se tornar alvo de ataque. Temos dois cockpits administrativos com os quais tratamos neste exercício. Um é o **cockpit SAP BTP** e o outro é o **console administrativo para Cloud Identity Services**. No cockpit do Trial BTP não temos acesso às funcionalidades globais de gerenciamento de usuários e segurança da conta. No console administrativo do Cloud Identity Services temos acesso. Neste exercício, verificaremos os usuários no console administrativo do Cloud Identity Services. Os serviços SAP Cloud Identity desempenham um papel crítico no acesso a aplicativos em nuvem SAP. Devido ao papel central dos serviços, é necessário reduzir o número de administradores com acesso total. As permissões dos serviços SAP Cloud Identity são baseadas no armazenamento interno do usuário e em seu conceito de permissão.

1. Abra o **console administrativo do Cloud Identity Services** em seus favoritos ou como descrito no primeiro exercício.

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Primeiro adicionaremos um novo usuário de teste. Navegue até **Usuários e autorizações -> Gerenciamento de usuários**
3. Clique no botão **+ Adicionar**

<br><img src="/exercises/ex2/images/ex200user1.png" width="70%">

4. Uma janela pop-up permitirá inserir as informações relevantes do usuário de teste. Você é livre para escolher o nome e o endereço de e-mail. Defina o status como ativo. Clique no botão **+ Adicionar**.

<br><img src="/exercises/ex2/images/ex200user2.png" width="70%">

5. Agora adicionamos o usuário recém-criado aos Administradores. Escolha o item de menu **Usuários e autorizações --> Administradores**.

<br><img src="/exercises/ex2/images/ex22.png" width="70%">

6. Clique em **Adicionar -> Usuário**

<br><img src="/exercises/ex2/images/ex20add.png" width="70%">

7. Adicione as informações do **Identificador** (endereço de e-mail) do novo usuário de teste na janela Adicionar administrador e clique no botão **Salvar**.

<br><img src="/exercises/ex2/images/ex200user3.png" width="70%">
   
7. Agora podemos verificar o Usuário e suas autorizações. A atribuição das seguintes autorizações é crítica.
Idealmente, você os gerenciará como parte do processo do ciclo de vida da identidade.
- Gerenciar provedores de identidade corporativa
- Gerenciar configuração do locatário
- Gerenciar usuários
  
<br><img src="/exercises/ex2/images/ex200user4.png" width="70%">

8. Remova as autorizações que não são mais necessárias. Se você remover todos eles, o usuário não será mais administrador e o nome será removido da lista à esquerda. Faremos isso agora. Desmarque todos os botões de opção. Em seguida, clique no botão **Salvar**.

<br><img src="/exercises/ex2/images/ex200user5.png" width="70%">

9. Agora você precisa confirmar suas alterações. Clique no botão **Ok**.

<br><img src="/exercises/ex2/images/ex200user6.png" width="70%">

O único administrador restante será o usuário da sua conta de teste.
Você não pode remover completamente as autorizações deste usuário, pois ele é o único que resta.
Por esta razão a autorização
- Gerenciar configuração do locatário
- Gerenciar configuração de locatário e atribuição de autorização aos usuários

está esmaecido.

<br><img src="/exercises/ex2/images/ex2_MTC.png" width="70%">


## Exercício 2.2 Definindo uma política de senha personalizada

Por padrão, os serviços SAP Cloud Identity vêm com 2 políticas de senha, Standard e Enterprise. Neste exercício você aprenderá como definir sua própria política de senhas, com base nos requisitos da sua empresa.

1. Abra o **console de administração do Cloud Identity Services**.

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Escolha o item de menu **Aplicativos e Recursos --> Políticas de Senha**

<br><img src="/exercises/ex2/images/ex2pp1.png" width="70%">

3. Clique no botão **Adicionar Política Personalizada**.

<br><img src="/exercises/ex2/images/ex2pp2.png" width="70%">

4. A caixa de diálogo **Política de senha personalizada** é exibida

<br><img src="/exercises/ex2/images/ex2pp3.png" width="70%">

5. Defina a força da política como **3**. Isto implica que esta política tem uma prioridade mais elevada do que as políticas existentes “Standard” e “Enterprise”. Isso se torna relevante quando um usuário acessa aplicativos com diferentes requisitos de política de senha. Uma política de senha com força 3 também será aceita por aplicativos que exigem força 1 ou 2.

💡 O serviço de autenticação de identidade não mede a força da política que você define. Cabe a você decidir quais propriedades são necessárias para que uma senha seja considerada forte

6. Decida o "Comportamento da senha". O usuário deve ser capaz de redefinir uma senha expirada com a antiga ou deve executar o processo de redefinição de senha?

7. Defina a "Contagem de grupos de caracteres necessários" como 3. Os serviços SAP Cloud Identity suportam 4 tipos de grupos de caracteres, letras maiúsculas, letras minúsculas, números e símbolos. Com esta configuração você especifica quantos grupos diferentes precisam fazer parte da senha.

8. Preencha os campos restantes da caixa de diálogo "Política de senha personalizada" e clique no botão **"Adicionar"**. Sua nova política de senha é adicionada ao topo da lista porque tem a maior resistência.

<br><img src="/exercises/ex2/images/ex2pp4.png" width="70%">

Agora você sabe como criar uma política de senha personalizada que pode ser usada para proteção adicional de seus aplicativos. Agora queremos adicionar a política de senha a um aplicativo.

9. Navegue até **Aplicativos e Recursos -> Aplicativos**. Selecione um aplicativo à esquerda e escolha no lado direito **Autenticação e Acesso -> Políticas**.

<br><img src="/exercises/ex2/images/addpp1.png" width="70%">

10. Escolha **Política de senha**

<br><img src="/exercises/ex2/images/addpp2.png" width="70%">

11. Selecione sua política de senha personalizada. Clique no botão **Salvar**.

Agora a nova política de senha está ativa para o aplicativo. Ele define as regras que você definiu para o comprimento e conteúdo da senha, bem como como os usuários podem atualizar e desbloquear senhas. 


## Exercício 2.3 Manter o acesso público aos aplicativos por meio de autorregistro desabilitado

Para cenários de empresa para consumidor (público), o autorregistro pode ser necessário. Por padrão, o autorregistro está desabilitado (valor = interno) e pode ser configurado por aplicação.
Os processos do ciclo de vida da identidade corporativa tornam o autorregistro indesejável na maioria dos cenários business-to-employee (B2E) e business-to-business (B2B). Recomendamos manter o autorregistro desabilitado (valor = interno). Gerencie ativamente os casos de uso que exigem a função.

Procedimento

1. Abra o **console de administração do Cloud Identity Services**.

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Em **Aplicativos e Recursos**, escolha o bloco **Aplicativos**.

<br><img src="/exercises/ex2/images/ex2selfreg1.png" width="70%">

3. Escolha o **aplicativo** que deseja editar.
4. Escolha a guia **Autenticação e acesso**.
5. Em **Autenticação**, escolha **Acesso ao Aplicativo do Usuário**.

<br><img src="/exercises/ex2/images/ex2selfreg2.png" width="70%">

6. Defina o botão de opção para os usuários que você deseja permitir o logon:
- Público
- Interno
- Privado

<br><img src="/exercises/ex2/images/ex2selfreg3.png" width="70%">
  
7. Salve sua seleção. A configuração padrão já é **Interna**. Por isso você não precisa alterá-lo.
8. Caso o aplicativo seja atualizado, o sistema apresenta a mensagem “Aplicativo - *nome do aplicativo*” atualizado.

## Exercício 2.4 Manter o Social Sign-On desativado

Para cenários de empresa para consumidor (público), o Social Sign-On pode ser necessário. Se ativado, os usuários poderão fazer logon com suas contas Apple, Google, Facebook, Twitter ou LinkedIn. Por padrão, o Social Sign-On está desabilitado, definido como Desativado e pode ser configurado por aplicativo.
Os processos do ciclo de vida da identidade corporativa tornam o login social indesejável na maioria dos cenários business-to-employee (B2E) e business-to-business (B2B).

Procedimento

1. Faça login no **console de administração do SAP Cloud Identity Services**.

<br><img src="/exercises/ex2/images/SCICockpit.png" width="70%">

2. Em **Aplicativos e Recursos**, escolha o bloco **Aplicativos**.

<br><img src="/exercises/ex2/images/ex2selfreg1.png" width="70%">

3. Escolha o **aplicativo** que deseja editar.
4. Escolha a guia **Autenticação e Acesso**.
5. Em **Autenticação**, ative ou desative **Social Sign-On** usando o botão de opção. Por padrão, ele deve estar desabilitado. Por isso você não precisa alterá-lo.

<br><img src="/exercises/ex2/images/ex2sso1.png" width="70%">

6. Após a atualização do aplicativo, o sistema apresenta a mensagem “Aplicativo - *nome do aplicativo*” atualizado.

Com o Social Sign-On, os usuários podem fazer logon no aplicativo por meio de um dos provedores sociais. Eles podem ver essa opção na página de login. Quais logotipos de provedores de identidade social aparecem na página de logon do aplicativo depende das configurações que você fez.

7. Efetue logout no **console administrativo do SCI**.

<br><img src="/exercises/ex1/images/SCI_logout.png" width="70%">

## Resumo

Neste exercício você aprendeu como identificar contas de usuário potencialmente desnecessárias. Além disso, você viu como definir políticas de senha personalizadas e como verificar diversas configurações relacionadas à autenticação de usuários.



Continue para - [Exercício 3 - Recomendações de segurança em relação ao log de auditoria](../ex3/README.md)
