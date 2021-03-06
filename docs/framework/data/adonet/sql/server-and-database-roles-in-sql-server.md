---
title: Роли сервера и базы данных в SQL Server
ms.date: 03/30/2017
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
ms.openlocfilehash: 9a563c2b448b07dc6536ff42a21c256195ba52fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="server-and-database-roles-in-sql-server"></a>Роли сервера и базы данных в SQL Server
Во всех версиях SQL Server используется безопасность на основе ролей, что позволяет назначать разрешения роли или группе пользователей, а не отдельным пользователям. Предопределенные роли сервера и предопределенные роли базы данных имеют предопределенный набор разрешений, назначенных для них.  
  
## <a name="fixed-server-roles"></a>Предопределенные роли сервера  
 Предопределенные роли сервера имеют предопределенный набор разрешений на уровне сервера. Они предназначены для использования в администрировании SQL Server, и разрешения, назначенные им, не могут быть изменены. Предопределенным ролям сервера могут назначаться имена входа без наличия учетной записи пользователя в базе данных.  
  
> [!IMPORTANT]
>  Предопределенная роль сервера `sysadmin` включает в себя все остальные роли и имеет неограниченную область действия. В эту роль следует включать только доверенных участников. Члены роли `sysadmin` обладают безотзывными правами администратора применительно ко всем базам данных и ресурсам сервера.  
  
 Тщательно обосновывайте решение по добавлению пользователей к предопределенным ролям сервера. Например, роль `bulkadmin` позволяет пользователям вставлять содержимое любого локального файла в таблицу, что может подвергнуть риску целостность данных. Полный список предопределенных ролей сервера и разрешения в разделе электронной документации по SQL Server.  
  
## <a name="fixed-database-roles"></a>Предопределенные роли базы данных  
 Предопределенные роли базы данных имеют предопределенный набор разрешений, разработанных для упрощения управления группами разрешений. Члены роли `db_owner` могут выполнять все действия по настройке конфигурации и обслуживанию базы данных.  
  
 Дополнительные сведения о предопределенных ролях SQL Server см. в следующих ресурсах.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[Роли уровня сервера](http://msdn.microsoft.com/library/ms188659.aspx) и [разрешения предопределенных ролей сервера](http://msdn.microsoft.com/library/ms175892.aspx) в электронной документации по SQL Server|Описывает предопределенные роли сервера и разрешения, связанные с ними в SQL Server.|  
|[Роли уровня базы данных](http://msdn.microsoft.com/library/ms189121.aspx) и [разрешения предопределенных ролей базы данных](http://msdn.microsoft.com/library/ms189612.aspx) в электронной документации по SQL Server|Описывает предопределенные роли базы данных и связанные с ними разрешения|  
  
## <a name="database-roles-and-users"></a>Роли и пользователи базы данных  
 Чтобы можно было работать с объектами базы данных, имена входа должны быть сопоставлены с учетными записями пользователей базы данных. После этого пользователи базы данных могут быть добавлены к ролям базы данных, наследуя все наборы разрешений, связанные с этими ролями. Можно предоставить все разрешения.  
  
 При разработке средств безопасности приложения также необходимо рассмотреть роль `public`, учетную запись пользователя `dbo` и учетную запись `guest`.  
  
### <a name="the-public-role"></a>Роль public  
 Роль `public` содержится в каждой базе данных, включая системные базы данных. Ее нельзя удалить, а также нельзя добавлять и удалять пользователей из нее. Разрешения, предоставленные роли `public`, наследуются всеми остальными пользователями и ролями, поскольку они принадлежат к роли `public` по умолчанию. Следует предоставлять роли `public` только разрешения, необходимые для всех пользователей.  
  
### <a name="the-dbo-user-account"></a>Учетная запись пользователя dbo  
 `dbo`, или владелец базы данных, представляет собой учетную запись пользователя, которая имеет неявно заданные разрешения на выполнение любых действий с базой данных. Члены предопределенной роли сервера `sysadmin` автоматически сопоставляются с `dbo`.  
  
> [!NOTE]
>  `dbo` совпадает с именем схемы, как описано в [владение и отделение пользователей от схем в SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md).  
  
 Учетную запись пользователя `dbo` часто путают с предопределенной ролью базы данных `db_owner`. Но областью действия `db_owner` является база данных, а областью действия `sysadmin` является весь сервер. Членство в роли `db_owner` не дает доступа к пользовательским привилегиям роли `dbo`.  
  
### <a name="the-guest-user-account"></a>Учетная запись пользователя guest  
 После прохождения пользователем проверки подлинности и получения разрешения на вход в экземпляр SQL Server в каждой базе данных должна существовать отдельная учетная запись пользователя, к которой пользователь должен получить доступ. В связи с требованием о существовании учетной записи пользователя в каждой базе данных предотвращается соединения пользователей с экземпляром SQL Server и получение доступа ко всем базам данных сервера. Существование учетной записи пользователя `guest` в базе данных дает возможность обойти данное требование, позволяя имени входа без учетной записи базы данных получить доступ к базе данных.  
  
 Учетная запись `guest` является встроенной учетной записью во всех версиях SQL Server. По умолчанию учетная запись guest в новых базах данных отключена. Если она включена, ее можно отключить путем отмены разрешения CONNECT, выполнив инструкцию REVOKE CONNECT FROM GUEST языка Transact-SQL.  
  
> [!IMPORTANT]
>  Следует избегать использования учетной записи `guest`. Все имена входа без собственных разрешений базы данных получают разрешения, предоставленные данной учетной записи. При необходимости использования учетной записи `guest` следует предоставить ей минимальные разрешения.  
  
 Дополнительные сведения об именах входа, пользователях и ролях SQL Server см. в следующих ресурсах.  
  
|Ресурс|Описание|  
|--------------|-----------------|  
|[Управление доступом и удостоверениями](http://msdn.microsoft.com/library/bb510418.aspx) в электронной документации по SQL Server|Содержит ссылки на разделы, описывающие участников, роли, учетные данные, защищаемые объекты и разрешения.|  
|[Субъекты](http://msdn.microsoft.com/library/ms181127.aspx) в электронной документации по SQL Server|Описывает участников и содержит ссылки на разделы, описывающие роли сервера и базы данных.|  
  
## <a name="see-also"></a>См. также  
 [Защита приложений ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Сценарии безопасности приложений в SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Проверка подлинности в SQL Server](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [Владение и отделение пользователей от схем в SQL Server](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [Авторизация и разрешения в SQL Server](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](http://go.microsoft.com/fwlink/?LinkId=217917)
