## Links video-aulas do canal elipse:

 - https://www.youtube.com/watch?v=wvXCEN5iaAg&list=PLoCAWpTf0fzXG8MQVpvq_5jf0b7L1zk05&index=32
 - https://www.youtube.com/watch?v=8YIBB7s9rYM&list=PLoCAWpTf0fzXG8MQVpvq_5jf0b7L1zk05&index=55
 - https://www.youtube.com/watch?v=ZO6XhfuHDcg&list=PLoCAWpTf0fzXG8MQVpvq_5jf0b7L1zk05&index=56
 - https://www.youtube.com/watch?v=-v-WKxL1lA8&list=PLoCAWpTf0fzXG8MQVpvq_5jf0b7L1zk05&index=56
 - https://www.youtube.com/watch?v=w7mLwDrjIhA&list=PLoCAWpTf0fzXG8MQVpvq_5jf0b7L1zk05&index=44
 - https://www.youtube.com/watch?v=IBD0XfFqcW0&list=PLoCAWpTf0fzXG8MQVpvq_5jf0b7L1zk05&index=38
 - https://www.youtube.com/watch?v=chq2GjBrA20&list=PLoCAWpTf0fzXG8MQVpvq_5jf0b7L1zk05&index=61 


Instalar Modbus simulator demo e fieldlogger

As bibliotecas auxiliam o desenvolvimento de projetos antes demorados e complexos a se tornarem simples e rápidos,
evitando a repetição de telas e objetos. Estas bibliotecas são também utilizadas para otimizar o tempo 
de manutenção da aplicação.

## Conteúdo:

- XControls
- XObjects
- Evento CustomConfig
- Tela Indexada
- Tipos não-convencionais para propriedades de XControls e XObjects

Bibliotecas: Servem para evitar repetição de código e tornar o desenvolvimento mais rapido.

## Criação de bibliotecas com XControl:
- botao direito xcontrol -> inserir xcontrol em -> Nova biblioteca -> Escolher a pasta onde sera salva
a biblioteca -> Podemos renomear o xcontrol para exaustor por exemplo.
- O objetivo de uma biblioteca é ter um objeto de modelo que pode ser replicado em varias telas.
- Botao direito em bibliotecas -> registrar bibliotecas carregadas.
- Um xcontrol representa uma classe, cada objeto inserido é uma nova instancia da classe.
- O xcontrol é responsavel por toda a parte grafica do objeto de referencia.
- Se for realizado uma alteração no objeto de referencia que é classe então as alterações serão 
aplicadas em todas as instancias aonde o objeto esta sendo usado.
- Podemos criar propriedades no xcontrol, por exemplo nome_exaustor, para criar uma nova propriedade basta clicar
em propriedade na parte inferior.
- Quando é criada uma nova propriedade é necessário fazer a associação para setar o texto digitado no valor da
variavel.
- Tudo oque está dentro do xcontrol não faz parte da aplicação, passará a fazer parte da aplicação somente depois
que for instanciado (referenciado) em alguma tela.
- Para fazer uma animação de uma figura é necessário criar uma tag dentro de objetos e dados.
- Para fazer a rotação é necessário criar uma nova propriedade, por exemplo uma propriedade chamada rotacao
que recebera um valor do tipo double.
- A propriedade nativa period determina a velocidade, pois ela determina o periodo do ponto inicial ate o ponto final.
	
## XObjects: 
- São responsaveis por toda a parte de dados do objeto de referencia, isso avita de ficar criando tag para cada xcontrol 
que for instanciado.
- É necessario passar as informações da tag criada para o exaustor deixando tudo dentro da biblioteca, para passar 
as informações da tag exaustor é necessário criar propriedades, como por exemplo rotacao e velocidade.
- Pode-ser criar uma propriedade chamada fonte por exemplo que servirá como uma ponte para acessar todas as propriedades
de um componente.
- xObjects não possuem parte visual.
- Quando for instanciado um xObject dentro dele já terá as tags demo de rotação e velocidade.
- Dentro de um unico xcontrol podemos ter texto, figura e animação.
- O método customConfig serve para executar um script no studio, exemplo ao clicar em algo aparecer uma msgbox.
- Podemos xObject já vinculado com o xControl.
- O método addObject serve para adicionar um objeto, o addObject tem tres propriedades, className, activate e objectName.
- Exemplo de className: "TagExaustor".
- O E3 não permite objetos com o mesmo nome contido no mesmo caminho.
- Para associar o xControl com o xObject é necessario criar variavel para receber o path.
- O E3 também trabalha com programação baseada em eventos.

## Diferenças principais entre XControl e XObject:
- Natureza: XControl é focado na criação de interfaces gráficas customizadas e na lógica de controle associada, enquanto XObject é mais genérico, utilizado para representar e manipular dados e configurações.

- Desenvolvimento: XControl requer habilidades de programação para desenvolver funcionalidades customizadas, enquanto XObject pode ser configurado através da interface gráfica do Elipse E3, além de suportar alguma programação em scripts.

- Uso: XControl é usado principalmente para criar interfaces de usuário interativas e visualmente ricas, enquanto XObject é utilizado para configurar e manipular dados e comportamentos dentro do sistema SCADA.

- Essas diferenças refletem a especialização e os propósitos distintos desses conceitos dentro do ambiente de desenvolvimento do Elipse E3 para aplicações SCADA.

## Tela indexada: 
  - Uma tela indexada é uma única tela que pode mostrar dados de varios equipamentos.
  - Um botão de liga e desliga deve ser bidirecional.
  - A fonte devemos deixar sempre dinamica.
 
 ## Método doModal:
  - xControl
 
 ## ModBus:
 - Serve para simular CLP conectados em uma rede.
 - Tipo IOTAG serve para dizer que esta esperando uma tag.
 - Uma propriedade pode receber um objeto inteiro ao invés de uma única propriedade.
 - Tags de comunicação.
 - Estudar sobre layers.
 - Para que haja a comunicação com os CLPS é necessário que seja instalado o driver apropriado.
 - Diagrama de associações: xObject -> xControl -> Tag
 - Toda vez que uma lib for alterada é necessário registrar ela.

 ## Criacao e vinculos entre XObject e XControl

Exemplo basico de criacao de um componente XControl associado a um XObject:

- Criar um componente do tipo XControl chamado de XCMotor.
- Adicionar um motor dentro do XControl criado.
- Criar um XObject chamado XOMotor com as propriedades: Temperatura do tipo Decimal e Estado do tipo Boolean.
- Criar uma propriedade para XCMotor chamada de Fonte do tipo XOMotor.
- Na propriedade OverrideFillColor do motor adicionado criar uma conexao do tipo digital
definindo as cores para o status ligado: 0, 255, 0 e desligado: 255, 0, 0 pegando os valores de XCMotor.Fonte.Estado
- Em Objetos de servidor -> Objetos de dados -> Dados -> Inserir o XOMotor criado.
- Nas propriedades do XOMotor instanciado em Objetos de servidor ir em associações e pegar os valores das tags correspondentes 
para Temperatura e Estado.

Explicacoes:

- Um XControl pode ter uma unica propriedade chamada Fonte do tipo XObject que foi criado para o XControl
- As associações de fonte de dados de origem, por exemplo de um CLP podem ser atribuídas para um XObject quando ele eh 
instanciado em Objetos de dados.
- No XControl as propriedades podem vir dele mesmo, exemplo: XCMotor.Fonte.Estado, as propriedades sempre
apontam para o proprio XControl atual + Fonte (poderia ser outro nome) +  propriedade do XObject.

## Exemplo de passagem de propriedade de uma tela para outra:

No evento de Click do motor adicionado no XControl inserir esse codigo para pegar os parametros do objeto clicado e 
chamar a tela de comandos passando os parametros.

```vbscript
Sub Motor_Click()
 Arg = XCMotor.Fonte.PathName
 Application.DoModal "TelaComandos", "Comando", , , , , Arg, 1 + 2 + 64 + 2048
End Sub
```

No evento OnPreShow da tela de comandos criada para as acoes do motor usar esse codigo para receber os parametros.

```vbscript
Sub TelaComandos_OnPreShow(Arg)
 Item("XCComandosMotor").Fonte = Arg
 Caption = Item("XCComandosMotor").Fonte.Name
End Sub
```

Symbol Factory 3 - Instalação

https://www.youtube.com/watch?v=9RxQt_pEoFI&list=PLVHMuBlUUtCNOfPWCTzmEdakPpleRpY5g&index=4&t=1s

O Elipse suporta imagens do tipo vetor em formato Metafile (wmf), essas imagens podem ter suas propriedades alteradas
em tempo de execução.

## Criacao do login e acesso as informacoes do usuario

Ao iniciar ou reiniciar o Viewer sera solicitado usuario e senha:

```vbscript
Sub Viewer_OnStartRunning()
 If Application.Login() then
  MsgBox "Login do usuário " & user & " realizado com sucesso!", vbinformation, "Informação de Login"
 Else
  MsgBox "Login Incorreto!", vbexclamation, "Informação de Login"
  Application.Exit()
 End If
End Sub
```

Se o login for bem sucedido o objeto usuario sera populado com as informacoes dele mesmo:

```vbscript
Sub Viewer_OnLogin()
 Application.GetObject("Dados.Usuario.XOUsuario").NomeDeUsuario = Application.User
 Application.GetObject("Dados.Usuario.XOUsuario").NomeCompletoDoUsuario = Application.GetFullUserName()
 Application.GetObject("Dados.Usuario.XOUsuario").NomeDoComputador = GetComputerName()
 Application.GetObject("Dados.Usuario.XOUsuario").DataHora = GetLocalTimeUTC()
End Sub
```