
#### 1. Jakie uprawnienia kryją się pod nazwą "Uprawnienia specjalne" widoczną wśród prostych ACL?
Czy to jest [to](http://www.omnisecu.com/windows-2003/managing-files-and-folders/special-permissions.php)?
#### 2. Jak wyznaczane są czynne uprawnienia dostępu do zasobów NTFS? Które operacje autoryzacji - zezwolenia czy odmowy - posiadają priorytet podczas kontroli dostępu?  Które uprawnienia - odziedziczone czy jawnie nadane mają wyższy priorytet?
Effective permissions are based on a local evaluation of the user's group membership, user privileges, and permissions. If the resource being queried is on a remote computer, the effective permissions displayed will not include permissions granted or denied to the user through the use of a local group on the remote computer. Tyle chyba starczy?  
Explicit permissions take precedence over inherited permissions, even inherited Deny permissions.  
Deny nadpisuje Allow.
#### 3. Jak w Windows 7 można zmienić uprawnienia dla kilku plików jednocześnie?
Należy umieścić wybrane pliki w jednym folderze i zmienić uprawnienia dla tego folderu
wybierając opcję propagacji uprawnień na dzieci.
#### 4.  Czy można w jakiś sposób przekopiewać listę ACL jednego pliku do drugiego?
```	
icacls nazwa_pliku /save aclfile
```
W pliku aclfile należy podmienieć w pierwszym wierszu nazwa_pliku na nazwę pliku, do którego kopiujemy acl.
```
icacls .\ /restore aclfile
```
#### 5.  Co oznacza uprawnienie WDAC (dostępne w poleceniu icacls)?
Write DAC.
DAC - dynamic access control - the ability to specify access control policies based on user, device, 
and resource claims. This makes for more flexible authentication for applications 
while maintaining security and compliance requirements.
https://technet.microsoft.com/en-us/library/dn408191(v=ws.11).aspx	
#### 6.  Jakie jest działanie funkcji Bypass Traverse Checking w NTFS?
This policy setting determines which users (or a process that acts on behalf of the user’s account) 
have permission to navigate an object path in the NTFS file system or in the registry without being 
checked for the Traverse Folder special access permission. This user right does not allow the user 
to list the contents of a folder. It only allows the user to traverse folders to access permitted 
files or subfolders.
#### 7.  Jak szyfrowany jest plik w systemie NTFS? Metodą symetryczną czy asymetryczną? Jakim kluczem? 
Gdzie ten klucz jest przechowywany i jak jest zabezpieczony?
	
Szyfrowany jest metodą symetryczną (algorytmem AES, 3DES lub DESX). Klucz jednorazowy wykorzystany
do szyfrowania przechowywany jest w nagłówku EFS zaszyfrowanego pliku. Klucz ten jest sam zaszyfrowany
kluczem publicznym (algorytm RSA) właściciela pliku, który przechowywany jest w certyfikacie EFS użytkownika.	
#### 8.  Co zawierają certyfikaty EFS użytkowników?
Klucz publiczny i prywatny użytkownika. Klucz prywatny jest uzyty do odszyfrowania klucza symetrycznego,
ktory to zostal zaszyfrowany kluczem publicznym. Ogolnie to gosciu na tym filmiku
https://www.youtube.com/watch?v=rnuCitzSgQ8 rozjebal temat o EFS. Jest tam bardziej pokazane jak to w praktyce
wyglada, ale na poczatku i pod koniec (od 10:57) jest przeglad od strony teoretycznej.
#### 9.  Jak umożliwić współdzielenie zaszyfrowanego pliku?
You can add extra authorized users to files, but not folders, and you can't add groups—just individuals. The process is very simple:
<ol>
    <li>Open the properties dialog for the file you want to add users to, then open the Advanced Attributes dialog box.</li>
    <li>If it's not already encrypted, encrypt it—you cannot add users until you've successfully encrypted the file.</li>
    <li>Click the Details button. You'll see an Encryption Details dialog that shows which users are currently authorized to open the file.</li>
    <li>Click the Add button. Select the user you want to grant access to and click OK. IF necessary, you can use the Find User button to search the local machine or Active Directory for the user and the associated certificate.</li>
</ol>
#### 10. Do czego służy systemowe narzędzie rekeywiz?
The Encrypting File System rekeying wizard allows the user to choose a certificate for EFS 
and to select and migrate existing files that will use the newly chosen certificate. 
It can also be used to migrate users in existing installations from software certificates
to smartcards. The wizard can also be used by an administrator or users themselves 
in recovery situations. It is more efficient than decrypting and reencrypting files.

[<<< back](./Readme.md)
