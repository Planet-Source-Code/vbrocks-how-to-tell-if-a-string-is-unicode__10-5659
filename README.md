<div align="center">

## How to tell if a String is Unicode


</div>

### Description

Identifies whether a string is encoded in Unicode.
 
### More Info
 
String.

Call the function passing it a string and it will return True if the String is encoded in Unicode, False if not.

Boolean: True or False


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[VBRocks](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/vbrocks.md)
**Level**          |Advanced
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |VB\.NET
**Category**       |[Strings](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/strings__10-26.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/vbrocks-how-to-tell-if-a-string-is-unicode__10-5659/archive/master.zip)





### Source Code

```
Private Function IsStringUnicode(ByVal str As String) As Boolean
 'Set it to False by default
 Dim bIsUnicode As Boolean = False
 'Setup Encodings
 Dim EncDefault As System.Text.Encoding = System.Text.Encoding.GetEncoding(0) 'String Default Encoding
 Dim EncUnicode As System.Text.Encoding = System.Text.Encoding.Unicode  'Encoding
 Dim bitesDefault As Byte() = EncDefault.GetBytes(str) 'Get the bytes of the string using the string's default encoding
 Dim bitesUnicode As Byte() = EncUnicode.GetBytes(str)
 Dim charsDefault As Char() = EncDefault.GetChars(bitesDefault) 'Get the characters of the default string
 Dim charsUnicode As Char() = EncUnicode.GetChars(bitesUnicode) 'Get the characters in unicode
 'Loop through all the characters and see if they all match.
 ' if any do not match, then it's unicode
 For i As Integer = 0 To charsDefault.Length - 1
  If charsDefault(i) <> charsUnicode(i) Then
  bIsUnicode = True
  'we found one that doesn't match, so exit the loop
  Exit For
  End If
 Next
 Return bIsUnicode
 End Function
```

