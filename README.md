## WS02-IS OpenIDConnect Federation Example
### Example of OpenIDConnect Federation between 2 instances of WSO2-IS

## Prerequisites
Docker

## Installation
```bash
docker-compose up
```

By running `docker-compose up` two docker containers will be created.  The Service Provider will need to be set-up to talk to an application built to use openIDConnect as an authentication mechanism. The Identity Provider, as the name states, is the federated identity provider used to authenticate the user.

The Service Provider will be running on port `9443`at `https://localhost:9443/carbon/`

The Identity Provider will be running on port `9444` at `https://localhost:9444/carbon/`

## Set-up

### Initial Configuration

During the `docker-compose` process, both `identity.xml` and `carbon.xml` are volumed in to the container to overwrite the default WSO2-IS settings.
#### carbon.xml
Due to port conflicts of running multiple instances of WSO2-IS, `carbon.xml` was updated to reflect the port change to `9444` 
```xml
<Offset>1</Offset>
```

The file can be found in `<IS_HOME>/repository/conf/carbon.xml`

More information regarding setting up the offset port can be found [here](https://docs.wso2.com/display/IS530/Default+Ports+of+WSO2+Products#DefaultPortsofWSO2Products-offset)

#### identity.xml
The `identity.xml` file has been updated to skip the consent screen when attempting to login a user. There's currently an exception scenario when you attempt login and have to display the consent.  The values that were changed can be found below.

```xml
<OpenIDSkipUserConsent>true</OpenIDSkipUserConsent>
```

```xml
 <SkipUserConsent>true</SkipUserConsent>
 ```

The file can be found in `<IS_HOME>/repository/conf/identity/identity.xml`

### Management Configuration

The set-up of these servers has already been documented by WSO2 and can be found [here](https://docs.wso2.com/display/IS530/Login+to+Identity+Server+Using+Another+Identity+Server+-+OAuth2).