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
short telaInicial = 10

// classe atual - qualquer valor diferente de 0 significa que um usuário está logado
short classeAtual

// este é o número da janela atual
short numeroJanelaAtual

// obtém o valor da classe atual
GetData(classeAtual, "Local HMI", LW, 9222, 1)

// obtém o número da janela atual
GetData(numeroJanelaAtual, "Local HMI", LW, 9050, 1) 

// se o usuário estiver desconectado e a janela atual não for a tela inicial então...
if classeAtual == 0 and numeroJanelaAtual <> telaInicial then 
  // Chama a tela inicial
  SetData(telaInicial, "Local HMI", LW, 0, 1)	
else 
end if

end macro_command
```