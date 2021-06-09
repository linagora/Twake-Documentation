# Database models

**APPLICATIONS**  
Represent an application in the database

```javascript
{
  //PK
  "company_id": uuid;
  "id": uuid;

  "identity": ApplicationIdentity;
  "api": ApplicationApi;
  "access": ApplicationAccess;
  "display": ApplicationDisplay;
  "publication": ApplicationPublication;
  "stats": ApplicationStatistics;
}

type ApplicationIdentity = {
  name: string;
  iconUrl: string;
  description: string;
  website: string;
  categories: string[];
  compatibility: "twake"[];
};

type ApplicationPublication = {
  published: boolean;
};

type ApplicationStatistics = {
  createdAt: number;
  updatedAt: number;
  version: number;
};

type ApplicationApi = {
  hooksUrl: string;
  allowedIps: string;
  privateKey: string;
};

type ApplicationAccess = {
  privileges: string[];
  capabilities: string[];
  hooks: string[];
};

type ApplicationDisplay = {
  twake: {};
};
```



**COMPANY\_APPLICATIONS**  
Represent an application in a company

```javascript
{
	"company_id": uuid;
	"application_id": uuid;
	"id": uuid;
	
	"created_at": number;
	"created_by": string; //Will be the default delegated user when doing actions on Twake
}
```

