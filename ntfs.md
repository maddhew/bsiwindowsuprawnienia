#### 1. Jakie uprawnienia kryj¹ siê pod nazw¹ "Uprawnienia specjalne" widoczn¹ wœród prostych ACL?
	Chuj wie

#### 2. Jak wyznaczane s¹ czynne uprawnienia dostêpu do zasobów NTFS? 
	Które operacje autoryzacji - zezwolenia czy odmowy - posiadaj¹ priorytet podczas kontroli dostêpu? 
	Które uprawnienia - odziedziczone czy jawnie nadane maj¹ priorytet?
	
	
	
#### 3. Jak w Windows 7 mo¿na zmieniæ uprawnienia dla kilku plików jednoczeœnie?

	Nale¿y umieœciæ wybrane pliki w jednym folderze i zmieniæ uprawnienia dla tego folderu
	wybieraj¹c opcjê propagacji uprawnieñ na dzieci.

#### 4.  Czy mo¿na w jakiœ sposób przekopiewaæ listê ACL jednego pliku do drugiego?
	
	icacls nazwa_pliku /save aclfile
	
	W pliku aclfile nale¿y podmienieæ w pierwszym wierszu nazwa_pliku na nazwê pliku, 
	do którego kopiujemy acl.
	
	icacls .\ /restore aclfile
	
#### 5.  Co oznacza uprawnienie WDAC (dostêpne w poleceniu icacls)?
	
	Write DAC.
	DAC - dynamic access control - the ability to specify access control policies based on user, device, 
	and resource claims. This makes for more flexible authentication for applications 
	while maintaining security and compliance requirements.
	https://technet.microsoft.com/en-us/library/dn408191(v=ws.11).aspx
	
#### 6.  Jakie jest dzia³anie funkcji Bypass Traverse Checking w NTFS?

	This policy setting determines which users (or a process that acts on behalf of the user’s account) 
	have permission to navigate an object path in the NTFS file system or in the registry without being 
	checked for the Traverse Folder special access permission. This user right does not allow the user 
	to list the contents of a folder. It only allows the user to traverse folders to access permitted 
	files or subfolders.

#### 7.  Jak szyfrowany jest plik w systemie NTFS? Metod¹ symetryczn¹ czy asymetryczn¹? Jakim kluczem? 
	Gdzie ten klucz jest przechowywany i jak jest zabezpieczony?
	
	Szyfrowany jest metod¹ symetryczn¹ (algorytmem AES, 3DES lub DESX). Klucz jednorazowy wykorzystany
	do szyfrowania przechowywany jest w nag³ówku EFS zaszyfrowanego pliku. Klucz ten jest sam zaszyfrowany
	kluczem publicznym (algorytm RSA) w³aœciciela pliku, który przechowywany jest w certyfikacie EFS u¿ytkownika.
	
#### 8.  Co zawieraj¹ certyfikaty EFS u¿ytkowników?

	Klucz publiczny u¿ytkownika (i jeszcze parê innych rzeczy, ale nie wiem czy to te¿ mamy wiedzieæ).

#### 9.  Jak umo¿liwiæ wspó³dzielenie zaszyfrowanego pliku?

	

#### 10. Do czego s³u¿y systemowe narzêdzie rekeywiz?
	The Encrypting File System rekeying wizard allows the user to choose a certificate for EFS 
	and to select and migrate existing files that will use the newly chosen certificate. 
	It can also be used to migrate users in existing installations from software certificates
	to smartcards. The wizard can also be used by an administrator or users themselves 
	in recovery situations. It is more efficient than decrypting and reencrypting files.