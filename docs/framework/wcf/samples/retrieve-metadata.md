---
title: Извлечение метаданных
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 17114eeb0f997545475d6903c21e408975c35d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="retrieve-metadata"></a>Извлечение метаданных
В этом образце показана реализация клиента, динамически извлекающего метаданные из службы для выбора конечной точки для взаимодействия. Этот пример построен на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md). Служба была изменена для предоставления двух конечных точек — конечную точку по базовому адресу с использованием `basicHttpBinding` привязки и защищенной конечной точки в {*baseaddress*} / secure с использованием `wsHttpBinding` привязки. Вместо выполнения настройки адресов и привязок конечных точек клиента, клиент динамически извлекает метаданные для службы с помощью класса <xref:System.ServiceModel.Description.MetadataExchangeClient>, а затем импортирует эти метаданные в виде <xref:System.ServiceModel.Description.ServiceEndpointCollection>, используя класс <xref:System.ServiceModel.Description.WsdlImporter>.  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 Клиентское приложение использует импортированную <xref:System.ServiceModel.Description.ServiceEndpointCollection>, чтобы создать клиенты для взаимодействия со службой. Клиентское приложение выполняет итерацию в каждой извлеченной конечной точке и взаимодействует с каждой конечной точкой, реализующей контракт `ICalculator`. Соответствующим адресу и привязке предоставляется извлеченная конечная точка; таким образом выполняется настройка взаимодействия клиента с каждой конечной точкой, как показано в следующем образце кода.  
  
```csharp   
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 В окне консольного приложения клиента отображаются операции, передаваемые в каждую из конечных точек, с указанием пути адреса и именем привязки.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1.  Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Чтобы создать выпуск решения C#, C++ или Visual Basic .NET, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Для запуска образца в конфигурации одного или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] образцов. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
  
## <a name="see-also"></a>См. также
