
#### 1. Co oznaczają udziały C$ oraz IPC$ i do czego są wykorzystywane?

DriveLetter$: This is a shared root partition or volume. Shared root partitions and volumes are displayed as the drive letter name appended with the dollar sign ($). For example, when drive letters C and D are shared, they are displayed as C$ and D$.  
IPC$: This is a resource that shares the named pipes that you must have for communication between programs. This resource cannot be deleted.  

#### 2. Jak przebiega zdalny dostęp do udziału udostępnionego użytkownikowi, którego lokalne konto (w systemie udostpęniającym udział) nie posiada hasła?


#### 3. Jakie operacje pozwalają wykonać polecenia net share, net view, net use, net file (net files) oraz net session (net sessions)?

**Net file** is used to show a list of open files on a server. The command can also be used to close a shared file and remove a file lock.  
**Net view** is used to show a list of computers and network devices on the network.  
The **net session** command is used to list or disconnect sessions between the computer and others on the network.  
The **net share** command is used to create, remove, and otherwise manage shared resources on the computer.  
The **net use** command is used to display information about shared resources on the network that you're currently connected to, as well as connect to new resources and disconnect from connected ones.  

#### 4. Obejrzyj istniejące reguły filtracji przychodzącego ruchu sieciowego w Zaporze sieciowej Windows. Dlaczego wszystkie predefiniowane reguły posiadają akcję "Zezwalaj"?

Ponieważ domyślna akcja dla połączeń przychodzących to "Zablokuj".

#### 5. Co oznaczają stosowane przez Microsoft pojęcia emisji pojedynczej i multiemisji?


[<<< back](./Readme.md)
