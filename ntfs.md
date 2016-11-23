#### 1. Jakie uprawnienia kryj� si� pod nazw� "Uprawnienia specjalne" widoczn� w�r�d prostych ACL?
	Chuj wie

#### 2. Jak wyznaczane s� czynne uprawnienia dost�pu do zasob�w NTFS? 
	Kt�re operacje autoryzacji - zezwolenia czy odmowy - posiadaj� priorytet podczas kontroli dost�pu? 
	Kt�re uprawnienia - odziedziczone czy jawnie nadane maj� priorytet?
	
	
	
#### 3. Jak w Windows 7 mo�na zmieni� uprawnienia dla kilku plik�w jednocze�nie?

	Nale�y umie�ci� wybrane pliki w jednym folderze i zmieni� uprawnienia dla tego folderu
	wybieraj�c opcj� propagacji uprawnie� na dzieci.

#### 4.  Czy mo�na w jaki� spos�b przekopiewa� list� ACL jednego pliku do drugiego?
	
	icacls nazwa_pliku /save aclfile
	
	W pliku aclfile nale�y podmienie� w pierwszym wierszu nazwa_pliku na nazw� pliku, 
	do kt�rego kopiujemy acl.
	
	icacls .\ /restore aclfile
	
#### 5.  Co oznacza uprawnienie WDAC (dost�pne w poleceniu icacls)?
	
	Write DAC.
	DAC - dynamic access control - the ability to specify access control policies based on user, device, 
	and resource claims. This makes for more flexible authentication for applications 
	while maintaining security and compliance requirements.
	https://technet.microsoft.com/en-us/library/dn408191(v=ws.11).aspx
	
#### 6.  Jakie jest dzia�anie funkcji Bypass Traverse Checking w NTFS?

	This policy setting determines which users (or a process that acts on behalf of the user�s account) 
	have permission to navigate an object path in the NTFS file system or in the registry without being 
	checked for the Traverse Folder special access permission. This user right does not allow the user 
	to list the contents of a folder. It only allows the user to traverse folders to access permitted 
	files or subfolders.

#### 7.  Jak szyfrowany jest plik w systemie NTFS? Metod� symetryczn� czy asymetryczn�? Jakim kluczem? 
	Gdzie ten klucz jest przechowywany i jak jest zabezpieczony?
	
	Szyfrowany jest metod� symetryczn� (algorytmem AES, 3DES lub DESX). Klucz jednorazowy wykorzystany
	do szyfrowania przechowywany jest w nag��wku EFS zaszyfrowanego pliku. Klucz ten jest sam zaszyfrowany
	kluczem publicznym (algorytm RSA) w�a�ciciela pliku, kt�ry przechowywany jest w certyfikacie EFS u�ytkownika.
	
#### 8.  Co zawieraj� certyfikaty EFS u�ytkownik�w?

	Klucz publiczny u�ytkownika (i jeszcze par� innych rzeczy, ale nie wiem czy to te� mamy wiedzie�).

#### 9.  Jak umo�liwi� wsp�dzielenie zaszyfrowanego pliku?

	

#### 10. Do czego s�u�y systemowe narz�dzie rekeywiz?
	The Encrypting File System rekeying wizard allows the user to choose a certificate for EFS 
	and to select and migrate existing files that will use the newly chosen certificate. 
	It can also be used to migrate users in existing installations from software certificates
	to smartcards. The wizard can also be used by an administrator or users themselves 
	in recovery situations. It is more efficient than decrypting and reencrypting files.