# -tLine-IDLArray-i-
#include &lt;FileConstants.au3> #include &lt;MsgBoxConstants.au3> #include &lt;StringConstants.au3> #include &lt;Array.au3> ;~ testit() ;~ Exit  Local $IDLFolder="C:\Program Files (x86)\Windows Kits\10\Include\10.0.17763.0\um\" Local $IDLFileName="UIAutomationClient.idl"  Local $IDLFullFileName = $IDLFolder &amp; $IDLFileName Local $IDLArray = FileReadToArray($IDLFullFileName) Local $iLineCount = @extended  Local $IDLAU3FullFileName=@ScriptDir &amp; "\" &amp; $IDLFileName $IDLAU3FullFileName=stringreplace($IDLAU3FullFileName,".idl",".au3")  If @error Then     MsgBox($MB_SYSTEMMODAL, "", "There was an error reading the file. @error: " &amp; @error) ; An error occurred reading the current script file.     exit EndIf  Local $hFileOpen = FileOpen($IDLAU3FullFileName, $FO_OVERWRITE ) If $hFileOpen = -1 Then     MsgBox($MB_SYSTEMMODAL, "", "An error occurred whilst writing the new au3 file.")     exit EndIf  ;~TODO: Naming prefixing Global $interfaceName Global $GUID Global $i=0  while $i &lt; $iLineCount - 1 ;~      consolewrite($i)     $tLine=$IDLArray[$i]      $blockType=0
