```vbscript
Sub CmbFuncionarios_OnStartRunning()
    Dim namesArray, index1, index2, tempName

    namesArray = Array("Julio", "Guedin", "Vinicius", "Ismael")

    For index1 = LBound(namesArray) To UBound(namesArray) - 1
        For index2 = index1 + 1 To UBound(namesArray)
            If namesArray(index1) > namesArray(index2) Then
                tempName = namesArray(index1)
                namesArray(index1) = namesArray(index2)
                namesArray(index2) = tempName
            End If
        Next
    Next

    For index1 = LBound(namesArray) To UBound(namesArray)
        AddItem namesArray(index1)
    Next
End Sub
```