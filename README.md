# LDAP


get-ciminstance win32_product | fl      фильтр установленного програмного обеспечения

get-ciminstance win32_product -Filter "NOT Vendor like '%Microsoft%'" | fl

Get-ADComputer  -Filter "DNSHostName -like 'SQL*'"

Get-ADGroup -Filter "adminCount -eq 1" | select Name

Get-ADUser -Filter {adminCount -eq '1' -and DoesNotRequirePreAuth -eq 'True'}

Get-ADUser -Filter "adminCount -eq '1'" -Properties * | where servicePrincipalName -ne $null | select SamAccountName,MemberOf,ServicePrincipalName | fl        поиск административных пользователей по имени субъекта службы (ServicePrincipalName)


Поиск description --->    ldapsearch -x -H ldap://10.129.107.44 -b "DC=INLANEFREIGHT,DC=LOCAL" "(&(objectCategory=person)(objectClass=user))" sAMAccountName description

nxc ldap 10.129.42.188 -u james.cross -p 'Academy_Student!' --query "(&(objectCategory=person)(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=128))" ""

