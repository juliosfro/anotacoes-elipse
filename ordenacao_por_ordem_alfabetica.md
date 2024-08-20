```vbscript
Sub CmbFuncionarios_OnStartRunning()
  Dim namesArray, index1, index2, tempName
    Dim arrayLength

    ' Define o array de nomes
    namesArray = Array("Julio", "Guedin", "Vinicius", "Ismael")
    
    ' Obtém o comprimento do array
    arrayLength = UBound(namesArray)
    
    ' Ordena o array usando Bubble Sort
    For index1 = arrayLength - 1 To 0 Step -1
        For index2 = 0 To index1 - 1
            If LCase(namesArray(index2)) > LCase(namesArray(index2 + 1)) Then
                ' Troca os elementos
                tempName = namesArray(index2)
                namesArray(index2) = namesArray(index2 + 1)
                namesArray(index2 + 1) = tempName
            End If
        Next
    Next

    ' Adiciona os itens ordenados ao ComboBox
    For index1 = 0 To arrayLength
        AddItem namesArray(index1)
    Next	
End Sub
```