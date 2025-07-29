# Json Export of a table

It saves the file beside the active workbook file but with the `.json` file extension. It's fast. It can be easily formatted in VS Code (`Shift`+`Alt`+`F`).

To use it, hit `Alt`+`F11` to get to the VBA code editor, open the code for your active worksheet, then paste it into the code window. Hit `F5` to run.
```visualbasic
Public Sub tojson()
    Dim fso As Object
    Set fso = CreateObject("Scripting.FileSystemObject")
    jsonFilename = fso.GetBaseName(ActiveWorkbook.Name) & ".json"
    fullFilePath = Application.ActiveWorkbook.Path & "\" & jsonFilename

    Dim fileStream As Object
    Set fileStream = CreateObject("ADODB.Stream")
    fileStream.Type = 2 'Specify stream type - we want To save text/string data.
    fileStream.Charset = "utf-8" 'Specify charset For the source text data.
    fileStream.Open 'Open the stream And write binary data To the object

    Dim wkb As Workbook
    Set wkb = ThisWorkbook

    Dim wks As Worksheet
    Set wks = wkb.Sheets(1)

    lcolumn = wks.Cells(1, Columns.Count).End(xlToLeft).Column
    lrow = wks.Cells(Rows.Count, "A").End(xlUp).Row
    Dim titles() As String
    ReDim titles(lcolumn)
    For i = 1 To lcolumn
        titles(i) = wks.Cells(1, i)
    Next i
    fileStream.WriteText "["
    dq = """"
    escapedDq = "\"""
    For j = 2 To lrow
        For i = 1 To lcolumn
            If i = 1 Then
                fileStream.WriteText "{"
            End If
            cellvalue = Replace(wks.Cells(j, i), dq, escapedDq)
            fileStream.WriteText dq & titles(i) & dq & ":" & dq & cellvalue & dq
            If i <> lcolumn Then
                fileStream.WriteText ","
            End If
        Next i
        fileStream.WriteText "}"
        If j <> lrow Then
            fileStream.WriteText ","
        End If
    Next j
    fileStream.WriteText "]"
    fileStream.SaveToFile fullFilePath, 2 'Save binary data To disk
    a = MsgBox("Saved to " & fullFilePath, vbOKOnly)
End Sub
```