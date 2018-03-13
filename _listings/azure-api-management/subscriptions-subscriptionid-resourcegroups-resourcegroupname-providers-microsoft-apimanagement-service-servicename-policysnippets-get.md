---
swagger: "2.0"
info:
  title: ApiManagementClient
  description: Use these REST APIs for performing operations on User entity in Azure
    API Management deployment. The User entity in API Management represents the developers
    that call the APIs of the products to which they are subscribed.
  version: 1.0.0
host: management.azure.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  ? /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.ApiManagement/service/{serviceName}/policySnippets
  : get:
      summary: PolicySnippets ListByService
      description: Lists all policy snippets
      operationId: PolicySnippets_ListByService
      parameters:
      - in: query
        name: No Name
      - in: query
        name: scope
        description: Policy scope
      responses:
        200:
          description: OK
      tags:
      - policy snippets
definitions:
  ErrorFieldContract:
    properties:
      code:
        description: This is a default description.
        type: get
      message:
        description: This is a default description.
        type: get
      target:
        description: This is a default description.
        type: get
  ErrorBodyContract:
    properties:
      code:
        description: This is a default description.
        type: get
      message:
        description: This is a default description.
        type: get
      details:
        description: This is a default description.
        type: get
  PolicySnippetsCollection:
    properties:
      value:
        description: This is a default description.
        type: get
  PolicySnippetContract:
    properties:
      name:
        description: This is a default description.
        type: get
      content:
        description: This is a default description.
        type: get
      toolTip:
        description: This is a default description.
        type: get
      scope:
        description: This is a default description.
        type: get
  RegionContract:
    properties:
      name:
        description: This is a default description.
        type: get
      isMasterRegion:
        description: This is a default description.
        type: get
  RegionListResult:
    properties:
      value:
        description: This is a default description.
        type: get
  ApiCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  ApiContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      serviceUrl:
        description: This is a default description.
        type: delete
      path:
        description: This is a default description.
        type: delete
      protocols:
        description: This is a default description.
        type: delete
  ApiEntityBaseContract:
    properties:
      description:
        description: This is a default description.
        type: delete
      type:
        description: This is a default description.
        type: delete
  ApiExportResult:
    properties:
      content:
        description: This is a default description.
        type: delete
      statusCode:
        description: This is a default description.
        type: delete
      requestId:
        description: This is a default description.
        type: delete
  ApiUpdateContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      serviceUrl:
        description: This is a default description.
        type: delete
      path:
        description: This is a default description.
        type: delete
      protocols:
        description: This is a default description.
        type: delete
  AuthenticationSettingsContract:
    properties: []
  OAuth2AuthenticationSettingsContract:
    properties:
      authorizationServerId:
        description: This is a default description.
        type: delete
      scope:
        description: This is a default description.
        type: delete
  OperationCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  OperationContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      method:
        description: This is a default description.
        type: delete
      urlTemplate:
        description: This is a default description.
        type: delete
  OperationEntityBaseContract:
    properties:
      templateParameters:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      responses:
        description: This is a default description.
        type: delete
  OperationUpdateContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      method:
        description: This is a default description.
        type: delete
      urlTemplate:
        description: This is a default description.
        type: delete
  ParameterContract:
    properties:
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      type:
        description: This is a default description.
        type: delete
      defaultValue:
        description: This is a default description.
        type: delete
      required:
        description: This is a default description.
        type: delete
      values:
        description: This is a default description.
        type: delete
  RepresentationContract:
    properties:
      contentType:
        description: This is a default description.
        type: delete
      sample:
        description: This is a default description.
        type: delete
  RequestContract:
    properties:
      description:
        description: This is a default description.
        type: delete
      queryParameters:
        description: This is a default description.
        type: delete
      headers:
        description: This is a default description.
        type: delete
      representations:
        description: This is a default description.
        type: delete
  ResultContract:
    properties:
      statusCode:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      representations:
        description: This is a default description.
        type: delete
  SubscriptionKeyParameterNamesContract:
    properties:
      header:
        description: This is a default description.
        type: delete
      query:
        description: This is a default description.
        type: delete
  AuthorizationServerCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  OAuth2AuthorizationServerContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      clientRegistrationEndpoint:
        description: This is a default description.
        type: delete
      authorizationEndpoint:
        description: This is a default description.
        type: delete
      authorizationMethods:
        description: This is a default description.
        type: delete
      clientAuthenticationMethod:
        description: This is a default description.
        type: delete
      tokenBodyParameters:
        description: This is a default description.
        type: delete
      tokenEndpoint:
        description: This is a default description.
        type: delete
      supportState:
        description: This is a default description.
        type: delete
  OAuth2AuthorizationServerUpdateContract:
    properties:
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      clientRegistrationEndpoint:
        description: This is a default description.
        type: delete
      authorizationEndpoint:
        description: This is a default description.
        type: delete
      authorizationMethods:
        description: This is a default description.
        type: delete
      clientAuthenticationMethod:
        description: This is a default description.
        type: delete
      tokenBodyParameters:
        description: This is a default description.
        type: delete
      tokenEndpoint:
        description: This is a default description.
        type: delete
      supportState:
        description: This is a default description.
        type: delete
      defaultScope:
        description: This is a default description.
        type: delete
  TokenBodyParameterContract:
    properties:
      name:
        description: This is a default description.
        type: delete
      value:
        description: This is a default description.
        type: delete
  BackendAuthorizationHeaderCredentials:
    properties:
      scheme:
        description: This is a default description.
        type: delete
      parameter:
        description: This is a default description.
        type: delete
  BackendBaseParameters:
    properties:
      title:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      resourceId:
        description: This is a default description.
        type: delete
  BackendCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  BackendContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      url:
        description: This is a default description.
        type: delete
      protocol:
        description: This is a default description.
        type: delete
  BackendCredentialsContract:
    properties:
      certificate:
        description: This is a default description.
        type: delete
      query:
        description: This is a default description.
        type: delete
      header:
        description: This is a default description.
        type: delete
  BackendProperties:
    properties:
      skipCertificateChainValidation:
        description: This is a default description.
        type: delete
      skipCertificateNameValidation:
        description: This is a default description.
        type: delete
  BackendProxyContract:
    properties:
      url:
        description: This is a default description.
        type: delete
      username:
        description: This is a default description.
        type: delete
      password:
        description: This is a default description.
        type: delete
  BackendResponse:
    properties:
      id:
        description: This is a default description.
        type: delete
  BackendUpdateParameters:
    properties:
      url:
        description: This is a default description.
        type: delete
      protocol:
        description: This is a default description.
        type: delete
  CertificateCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  CertificateContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      subject:
        description: This is a default description.
        type: delete
      thumbprint:
        description: This is a default description.
        type: delete
      expirationDate:
        description: This is a default description.
        type: delete
  CertificateCreateOrUpdateParameters:
    properties:
      data:
        description: This is a default description.
        type: delete
      password:
        description: This is a default description.
        type: delete
  CertificateInformation:
    properties:
      expiry:
        description: This is a default description.
        type: post
      thumbprint:
        description: This is a default description.
        type: post
      subject:
        description: This is a default description.
        type: post
  HostnameConfiguration:
    properties:
      type:
        description: This is a default description.
        type: post
      hostname:
        description: This is a default description.
        type: post
  VirtualNetworkConfiguration:
    properties:
      vnetid:
        description: This is a default description.
        type: post
      subnetname:
        description: This is a default description.
        type: post
      subnetResourceId:
        description: This is a default description.
        type: post
      location:
        description: This is a default description.
        type: post
  AdditionalRegion:
    properties:
      location:
        description: This is a default description.
        type: post
      skuType:
        description: This is a default description.
        type: post
      skuUnitCount:
        description: This is a default description.
        type: post
      staticIPs:
        description: This is a default description.
        type: post
  ApiManagementServiceManageDeploymentsParameters:
    properties:
      location:
        description: This is a default description.
        type: post
      skuType:
        description: This is a default description.
        type: post
      skuUnitCount:
        description: This is a default description.
        type: post
      additionalLocations:
        description: This is a default description.
        type: post
      vpnType:
        description: This is a default description.
        type: post
  ApiManagementServiceBackupRestoreParameters:
    properties:
      storageAccount:
        description: This is a default description.
        type: post
      accessKey:
        description: This is a default description.
        type: post
      containerName:
        description: This is a default description.
        type: post
      backupName:
        description: This is a default description.
        type: post
  ApiManagementServiceProperties:
    properties:
      publisherEmail:
        description: This is a default description.
        type: post
      publisherName:
        description: This is a default description.
        type: post
      provisioningState:
        description: This is a default description.
        type: post
      targetProvisioningState:
        description: This is a default description.
        type: post
      createdAtUtc:
        description: This is a default description.
        type: post
      runtimeUrl:
        description: This is a default description.
        type: post
      portalUrl:
        description: This is a default description.
        type: post
      managementApiUrl:
        description: This is a default description.
        type: post
      scmUrl:
        description: This is a default description.
        type: post
      addresserEmail:
        description: This is a default description.
        type: post
  ApiManagementServiceSkuProperties:
    properties:
      name:
        description: This is a default description.
        type: post
      capacity:
        description: This is a default description.
        type: post
  ApiManagementServiceResource:
    properties:
      etag:
        description: This is a default description.
        type: post
  Resource:
    properties:
      id:
        description: This is a default description.
        type: post
      name:
        description: This is a default description.
        type: post
      type:
        description: This is a default description.
        type: post
      location:
        description: This is a default description.
        type: post
      tags:
        description: This is a default description.
        type: post
  ApiManagementServiceUpdateParameters:
    properties:
      tags:
        description: This is a default description.
        type: post
  ApiManagementServiceListResult:
    properties:
      value:
        description: This is a default description.
        type: post
      nextLink:
        description: This is a default description.
        type: post
  ApiManagementServiceGetSsoTokenResult:
    properties:
      redirect_uri:
        description: This is a default description.
        type: post
  ApiManagementServiceCheckNameAvailabilityParameters:
    properties:
      name:
        description: This is a default description.
        type: post
  ApiManagementServiceNameAvailabilityResult:
    properties:
      nameAvailable:
        description: This is a default description.
        type: post
      message:
        description: This is a default description.
        type: post
      reason:
        description: This is a default description.
        type: post
  ApiManagementServiceUploadCertificateParameters:
    properties:
      type:
        description: This is a default description.
        type: post
      certificate:
        description: This is a default description.
        type: post
      certificate_password:
        description: This is a default description.
        type: post
  ApiManagementServiceUpdateHostnameParameters:
    properties:
      update:
        description: This is a default description.
        type: post
      delete:
        description: This is a default description.
        type: post
  ErrorResponse:
    properties:
      code:
        description: This is a default description.
        type: post
      message:
        description: This is a default description.
        type: post
  Operation:
    properties:
      name:
        description: This is a default description.
        type: post
  OperationListResult:
    properties:
      value:
        description: This is a default description.
        type: post
      nextLink:
        description: This is a default description.
        type: post
  GroupCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  GroupContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      builtIn:
        description: This is a default description.
        type: delete
      type:
        description: This is a default description.
        type: delete
      externalId:
        description: This is a default description.
        type: delete
  GroupCreateParameters:
    properties:
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      type:
        description: This is a default description.
        type: delete
      externalId:
        description: This is a default description.
        type: delete
  GroupUpdateParameters:
    properties:
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      type:
        description: This is a default description.
        type: delete
      externalId:
        description: This is a default description.
        type: delete
  IdentityProviderContract:
    properties:
      clientId:
        description: This is a default description.
        type: delete
      clientSecret:
        description: This is a default description.
        type: delete
      type:
        description: This is a default description.
        type: delete
      allowedTenants:
        description: This is a default description.
        type: delete
  IdentityProviderList:
    properties:
      value:
        description: This is a default description.
        type: delete
  IdentityProviderUpdateParameters:
    properties:
      clientId:
        description: This is a default description.
        type: delete
      clientSecret:
        description: This is a default description.
        type: delete
      allowedTenants:
        description: This is a default description.
        type: delete
  LoggerCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  LoggerCreateParameters:
    properties:
      type:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      credentials:
        description: This is a default description.
        type: delete
      isBuffered:
        description: This is a default description.
        type: delete
  LoggerResponse:
    properties:
      id:
        description: This is a default description.
        type: delete
      type:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      credentials:
        description: This is a default description.
        type: delete
      isBuffered:
        description: This is a default description.
        type: delete
  LoggerUpdateParameters:
    properties:
      type:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      credentials:
        description: This is a default description.
        type: delete
      isBuffered:
        description: This is a default description.
        type: delete
  ConnectivityStatusContract:
    properties:
      name:
        description: This is a default description.
        type: get
      status:
        description: This is a default description.
        type: get
      error:
        description: This is a default description.
        type: get
      lastUpdated:
        description: This is a default description.
        type: get
      lastStatusChange:
        description: This is a default description.
        type: get
  NetworkStatusContract:
    properties:
      dnsServers:
        description: This is a default description.
        type: get
      connectivityStatus:
        description: This is a default description.
        type: get
  OpenIdConnectProviderCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  OpenidConnectProviderContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      metadataEndpoint:
        description: This is a default description.
        type: delete
      clientId:
        description: This is a default description.
        type: delete
      clientSecret:
        description: This is a default description.
        type: delete
  OpenidConnectProviderCreateContract:
    properties:
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      metadataEndpoint:
        description: This is a default description.
        type: delete
      clientId:
        description: This is a default description.
        type: delete
      clientSecret:
        description: This is a default description.
        type: delete
  OpenidConnectProviderUpdateContract:
    properties:
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      metadataEndpoint:
        description: This is a default description.
        type: delete
      clientId:
        description: This is a default description.
        type: delete
      clientSecret:
        description: This is a default description.
        type: delete
  ProductCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  ProductContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      terms:
        description: This is a default description.
        type: delete
      subscriptionRequired:
        description: This is a default description.
        type: delete
      approvalRequired:
        description: This is a default description.
        type: delete
      subscriptionsLimit:
        description: This is a default description.
        type: delete
      state:
        description: This is a default description.
        type: delete
  ProductUpdateParameters:
    properties:
      name:
        description: This is a default description.
        type: delete
      description:
        description: This is a default description.
        type: delete
      terms:
        description: This is a default description.
        type: delete
      subscriptionRequired:
        description: This is a default description.
        type: delete
      approvalRequired:
        description: This is a default description.
        type: delete
      subscriptionsLimit:
        description: This is a default description.
        type: delete
      state:
        description: This is a default description.
        type: delete
  PropertyCollection:
    properties:
      value:
        description: This is a default description.
        type: delete
      count:
        description: This is a default description.
        type: delete
      nextLink:
        description: This is a default description.
        type: delete
  PropertyContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      name:
        description: This is a default description.
        type: delete
      value:
        description: This is a default description.
        type: delete
      tags:
        description: This is a default description.
        type: delete
      secret:
        description: This is a default description.
        type: delete
  PropertyCreateParameters:
    properties:
      name:
        description: This is a default description.
        type: delete
      value:
        description: This is a default description.
        type: delete
      tags:
        description: This is a default description.
        type: delete
      secret:
        description: This is a default description.
        type: delete
  PropertyUpdateParameters:
    properties:
      name:
        description: This is a default description.
        type: delete
      value:
        description: This is a default description.
        type: delete
      tags:
        description: This is a default description.
        type: delete
      secret:
        description: This is a default description.
        type: delete
  QuotaCounterCollection:
    properties:
      value:
        description: This is a default description.
        type: patch
      count:
        description: This is a default description.
        type: patch
      nextLink:
        description: This is a default description.
        type: patch
  QuotaCounterContract:
    properties:
      counterKey:
        description: This is a default description.
        type: patch
      periodKey:
        description: This is a default description.
        type: patch
      periodStartTime:
        description: This is a default description.
        type: patch
      periodEndTime:
        description: This is a default description.
        type: patch
  QuotaCounterValueContract:
    properties:
      callsCount:
        description: This is a default description.
        type: patch
      kbTransferred:
        description: This is a default description.
        type: patch
  ReportCollection:
    properties:
      value:
        description: This is a default description.
        type: get
      count:
        description: This is a default description.
        type: get
      nextLink:
        description: This is a default description.
        type: get
  ReportRecordContract:
    properties:
      name:
        description: This is a default description.
        type: get
      timestamp:
        description: This is a default description.
        type: get
      interval:
        description: This is a default description.
        type: get
      country:
        description: This is a default description.
        type: get
      region:
        description: This is a default description.
        type: get
      zip:
        description: This is a default description.
        type: get
      userId:
        description: This is a default description.
        type: get
      productId:
        description: This is a default description.
        type: get
      apiId:
        description: This is a default description.
        type: get
      operationId:
        description: This is a default description.
        type: get
  SubscriptionCollection:
    properties:
      value:
        description: This is a default description.
        type: post
      count:
        description: This is a default description.
        type: post
      nextLink:
        description: This is a default description.
        type: post
  SubscriptionContract:
    properties:
      id:
        description: This is a default description.
        type: post
      userId:
        description: This is a default description.
        type: post
      productId:
        description: This is a default description.
        type: post
      name:
        description: This is a default description.
        type: post
      state:
        description: This is a default description.
        type: post
      createdDate:
        description: This is a default description.
        type: post
      startDate:
        description: This is a default description.
        type: post
      expirationDate:
        description: This is a default description.
        type: post
      endDate:
        description: This is a default description.
        type: post
      notificationDate:
        description: This is a default description.
        type: post
  SubscriptionCreateParameters:
    properties:
      userId:
        description: This is a default description.
        type: post
      productId:
        description: This is a default description.
        type: post
      name:
        description: This is a default description.
        type: post
      primaryKey:
        description: This is a default description.
        type: post
      secondaryKey:
        description: This is a default description.
        type: post
      state:
        description: This is a default description.
        type: post
  SubscriptionUpdateParameters:
    properties:
      userId:
        description: This is a default description.
        type: post
      productId:
        description: This is a default description.
        type: post
      expirationDate:
        description: This is a default description.
        type: post
      name:
        description: This is a default description.
        type: post
      primaryKey:
        description: This is a default description.
        type: post
      secondaryKey:
        description: This is a default description.
        type: post
      state:
        description: This is a default description.
        type: post
      stateComment:
        description: This is a default description.
        type: post
  AccessInformationContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      primaryKey:
        description: This is a default description.
        type: delete
      secondaryKey:
        description: This is a default description.
        type: delete
      enabled:
        description: This is a default description.
        type: delete
  AccessInformationUpdateParameters:
    properties:
      enabled:
        description: This is a default description.
        type: delete
  DeployConfigurationParameters:
    properties:
      branch:
        description: This is a default description.
        type: delete
      force:
        description: This is a default description.
        type: delete
  OperationResultContract:
    properties:
      id:
        description: This is a default description.
        type: delete
      status:
        description: This is a default description.
        type: delete
      started:
        description: This is a default description.
        type: delete
      updated:
        description: This is a default description.
        type: delete
      resultInfo:
        description: This is a default description.
        type: delete
  SaveConfigurationParameter:
    properties:
      branch:
        description: This is a default description.
        type: delete
      force:
        description: This is a default description.
        type: delete
  TenantConfigurationSyncStateContract:
    properties:
      branch:
        description: This is a default description.
        type: delete
      commitId:
        description: This is a default description.
        type: delete
      isExport:
        description: This is a default description.
        type: delete
      isSynced:
        description: This is a default description.
        type: delete
      isGitEnabled:
        description: This is a default description.
        type: delete
      syncDate:
        description: This is a default description.
        type: delete
      configurationChangeDate:
        description: This is a default description.
        type: delete
  GenerateSsoUrlResult:
    properties:
      value:
        description: This is a default description.
        type: get
  UserCollection:
    properties:
      value:
        description: This is a default description.
        type: get
      count:
        description: This is a default description.
        type: get
      nextLink:
        description: This is a default description.
        type: get
  UserContract:
    properties:
      id:
        description: This is a default description.
        type: get
      firstName:
        description: This is a default description.
        type: get
      lastName:
        description: This is a default description.
        type: get
      email:
        description: This is a default description.
        type: get
      state:
        description: This is a default description.
        type: get
      registrationDate:
        description: This is a default description.
        type: get
      note:
        description: This is a default description.
        type: get
      identities:
        description: This is a default description.
        type: get
  UserCreateParameters:
    properties:
      email:
        description: This is a default description.
        type: get
      password:
        description: This is a default description.
        type: get
      firstName:
        description: This is a default description.
        type: get
      lastName:
        description: This is a default description.
        type: get
      state:
        description: This is a default description.
        type: get
      note:
        description: This is a default description.
        type: get
  UserIdentityCollection:
    properties:
      value:
        description: This is a default description.
        type: get
  UserIdentityContract:
    properties:
      provider:
        description: This is a default description.
        type: get
      id:
        description: This is a default description.
        type: get
  UserUpdateParameters:
    properties:
      email:
        description: This is a default description.
        type: get
      password:
        description: This is a default description.
        type: get
      firstName:
        description: This is a default description.
        type: get
      lastName:
        description: This is a default description.
        type: get
      state:
        description: This is a default description.
        type: get
      note:
        description: This is a default description.
        type: get
x-collection-name: Azure API Management
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---