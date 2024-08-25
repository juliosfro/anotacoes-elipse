## Criar trigger para alterar janela 

Clicar na aba Object -> PLC Control -> Attribute Type -> Change Window -> Trigger -> Address -> LW 0

Habilitar -> Clear data after window changed

## Definir tempo de execucao da macro

Habilitar -> Periodical execution -> Time interval 50 x 100 
Habilitar -> Execute one time when HMI starts

## Macro para retornar a tela inicial caso o usuario seja deslogado de forma automatica na IHM.

```vbscript
macro_command main()

// Define variavel tela inicial sendo a janela numero 10
short numeroTelaInicial = 10

// Qualquer valor diferente de 0 significa que um usuário está logado
short usuarioLogado = 0

// Este é o número da janela atual
short numeroJanelaAtual = 0

// Obtém o número do status do usuario
GetData(usuarioLogado, "Local HMI", LW, 9222, 1)

// Obtém o número da janela atual
GetData(numeroJanelaAtual, "Local HMI", LW, 9050, 1) 

// Se o usuário estiver desconectado e a janela atual não for a tela inicial então...
if usuarioLogado == 0 and numeroJanelaAtual <> numeroTelaInicial then 
  // Chama a tela inicial
  SetData(numeroTelaInicial, "Local HMI", LW, 0, 1) 
end if

end macro_command
```