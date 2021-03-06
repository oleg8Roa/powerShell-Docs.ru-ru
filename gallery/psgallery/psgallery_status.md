Состояние коллекции PowerShell
=========================


## 10.08.2016 — устранена ошибка: не удавалось отправлять электронные письма на адрес cgadmin@microsoft.com

__Сводка влияния__. С 05.08.2016 по 10.08.2016 клиентам не удавалось отправлять электронные письма по адресу cgadmin@microsoft.com или использовать функцию "Обратная связь".  
__Первопричина__. Инженеры выявили, что причина состояла в изменении конфигурации учетной записи электронной почты.  
__Решение__. Инженеры устранили проблему в конфигурации.  
__Дальнейшие действия__. Если вы использовали ссылку "Обратная связь" или отправляли почту по адресу cgadmin@microsoft.com в это время и не получили ответа, повторите попытку. Благодарим за терпение.



## 13.07.2016 — сбой скачивания элементов

__Сводка влияния__. С 11.07.2016 по 13.07.2016 у ряда клиентов возникали проблемы со скачиванием элементов из коллекции PowerShell. Скорее всего, проблема проявлялась в виде следующего сообщения об ошибке, возвращаемого из Install-Module/Install-Script и Save-Module/Save-Script.

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__Предварительная первопричина__. Инженеры выявили проблему в сети доставки содержимого Azure (CDN), развернутой для коллекции PowerShell 11.07.2016.  
__Устранение рисков__. Инженеры отключили Azure CDN в коллекции PowerShell.  
__Дальнейшие действия__. Мы находимся в процессе поиска первопричины и разрабатываем решение, чтобы предотвратить появление проблемы в будущем.


## 19.05.2016 — сбой скачивания элементов
__Сводка влияния__. С 17.05.2016 по 19.05.2016 у ряда клиентов возникали проблемы со скачиванием элементов из коллекции PowerShell. Скорее всего, проблема проявлялась в виде следующего сообщения об ошибке, возвращаемого из Install-Module/Install-Script и Save-Module/Save-Script.

```PowerShell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

__Предварительная первопричина__. Инженеры обнаружили сбой в базовом поставщике сети доставки содержимого Azure (CDN), развернутой для коллекции PowerShell 17.05.2016.  
__Устранение рисков__. Инженеры отключили Azure CDN в коллекции PowerShell.  
__Дальнейшие действия__. Мы находимся в процессе поиска первопричины и разрабатываем решение, чтобы предотвратить появление проблемы в будущем.


<!--HONumber=Sep16_HO2-->


