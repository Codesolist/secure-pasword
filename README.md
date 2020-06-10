# secure-pasword
detaylı anlatım için: https://www.alperenguney.com.tr/guvenli-sifre-olusturma-yollari/

Secure Password PowerShell Code:

Function GuvenliSifreniz ([Parameter(Mandatory=$true)][int]$PasswordLenght)
{
Add-Type -AssemblyName System.Web
$PassComplexCheck = $false
do {
$newPassword=[System.Web.Security.Membership]::GeneratePassword($PasswordLenght,1)
If ( ($newPassword -cmatch "[A-Z\p{Lu}\s]") `
-and ($newPassword -cmatch "[a-z\p{Ll}\s]") `
-and ($newPassword -match "[\d]") `
-and ($newPassword -match "[^\w]")
)
{
$PassComplexCheck=$True
}
} While ($PassComplexCheck -eq $false)
return $newPassword
}
GuvenliSifreniz (10)
