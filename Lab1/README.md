New-AzResourceGroup `
>>   -Name azuregroup `
>>   -Location "Central US" 

New-AzResourceGroupDeployment `
>>   -Name deployproject `
>>   -ResourceGroupName azuregroup `
>>   -TemplateFile azuredeploy.json `
>>   -TemplateParameterFile azuredeploy.parameters.json    