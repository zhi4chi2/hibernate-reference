# initiateService(Map configurationValues, ServiceRegistryImplementor registry)
1. hibernate.connection.provider_class
1. hibernate.connection.datasource
1. hibernate.c3p0
1. hibernate.proxool
1. hibernate.hikari
1. 如果设置了 hibernate.connection.url 则使用 DriverManagerConnectionProviderImpl
1. UserSuppliedConnectionProviderImpl
