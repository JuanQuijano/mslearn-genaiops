  (✓) Done: Resource group: rg-dev-trail-guide (3.422s)
  (✓) Done: Foundry: ai-account-czv4bse4ocrky (24.965s)
  (✓) Done: Log Analytics workspace: logs-czv4bse4ocrky (24.048s)
  (✓) Done: Azure AI Services Model Deployment: ai-account-czv4bse4ocrky/gpt-4.1-mini (3.17s)
  (✓) Done: Azure AI Services Model Deployment: ai-account-czv4bse4ocrky/gpt-4.1 (4.732s)
  (✓) Done: Foundry project: ai-account-czv4bse4ocrky/ai-project-dev-trail-guide (7.779s)
  (✓) Done: Application Insights: appi-czv4bse4ocrky (4.421s)
  (✓) Done: Foundry project connection: ai-account-czv4bse4ocrky/ai-project-dev-trail-guide/appi-connection (1.347s)
  (✓) Done: Container Registry: crczv4bse4ocrky (20.271s)
  (✓) Done: Foundry project connection: ai-account-czv4bse4ocrky/ai-project-dev-trail-guide/acr-connection (2.484s)
  (✓) Done: Foundry capability host: ai-account-czv4bse4ocrky/agents (8m59.529s)

Service principal
  {
  "appId": "dd5c1cc1-91a5-489f-9584-ab490283ec0d",
  "displayName": "github-agent-evaluator-trainer",
  "password": "<redacted>",
  "subscriptionId": "d1afe0fd-ca41-4b75-857e-e6f68052ad2c"
  "tenant": "da51a5d1-9b62-4a99-bcca-a0617f290b10"
}

 az role assignment create --assignee "dd5c1cc1-91a5-489f-9584-ab490283ec0d" --role "Azure AI User" --scope "/subscriptions/d1afe0fd-ca41-4b75-857e-e6f68052ad2c/resourceGroups/rg-dev-trail-guide/providers/Microsoft.CognitiveServices/accounts/github-agent-evaluator-trainer"


az ad app federated-credential create --id "dd5c1cc1-91a5-489f-9584-ab490283ec0d" --parameters @federated-credential.json 
Remove-Item federated-credential.json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications('1e419370-7b84-4de9-8411-9aa9d6c325d3')/federatedIdentityCredentials/$entity",
  "audiences": [
    "api://AzureADTokenExchange"
  ],
  "description": null,
  "id": "7a8084ee-3d95-4971-ab80-8fdc9e24bcd3",
  "issuer": "https://token.actions.githubusercontent.com",
  "name": "github-actions",
  "subject": "repo:JuanQuijano/mslearn-genaiops:ref:refs/heads/main"
}

az ad app federated-credential create --id "dd5c1cc1-91a5-489f-9584-ab490283ec0d" --parameters @federated-credential-pr.json
Remove-Item federated-credential-pr.json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#applications('1e419370-7b84-4de9-8411-9aa9d6c325d3')/federatedIdentityCredentials/$entity",
  "audiences": [
    "api://AzureADTokenExchange"
  ],
  "description": null,
  "id": "85e189af-efd0-444e-8341-54d13cc2d960",
  "issuer": "https://token.actions.githubusercontent.com",
  "name": "github-actions-pr",
  "subject": "repo:JuanQuijano/mslearn-genaiops:pull_request"
}