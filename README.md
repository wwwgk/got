{
  "swagger": "2.0",
  "info": {
    "version": "service",
    "title": "CE21 Service API Reference",
    "description": ""
  },
  "host": "api.ce21.com",
  "schemes": [
    "https"
  ],
  "paths": {
    "/service/Categories": {
      "get": {
        "tags": [
          "Categories"
        ],
        "summary": "Get All Categories for Tenant",
        "operationId": "Categories_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Category"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Categories/{categoryId}": {
      "get": {
        "tags": [
          "Categories"
        ],
        "summary": "Get Category",
        "description": "Get single category",
        "operationId": "Categories_GetCategory",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "categoryId",
            "in": "path",
            "description": "Id of Category",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Category"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Categories": {
      "get": {
        "tags": [
          "Categories"
        ],
        "summary": "Get All Categories for a Single Product",
        "description": "Get all categories for a single product.",
        "operationId": "Categories_GetProductCategories",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product Id",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Category"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Categories/{categoryId}": {
      "post": {
        "tags": [
          "Categories"
        ],
        "summary": "Add a Category to a Product",
        "description": "Adds a category to a product",
        "operationId": "Categories_PostCategoryToProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to be related.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "categoryId",
            "in": "path",
            "description": "Category to add to the Product.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Category"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Categories"
        ],
        "summary": "Remove Category from Product",
        "description": "Remove single Category from a Product",
        "operationId": "Categories_RemoveCategoryFromProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "ProductId to remove from.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "categoryId",
            "in": "path",
            "description": "CategoryId to be removed.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Companies": {
      "get": {
        "tags": [
          "Companies"
        ],
        "summary": "Get All Companies by Search",
        "description": "Get all Companies for tenant.",
        "operationId": "Companies_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "fromDate",
            "in": "query",
            "description": "Search records updated since the fromDate. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "toDate",
            "in": "query",
            "description": "Search records updated before the toDate. This is used with fromDate to choose a range. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "keyword",
            "in": "query",
            "description": "Search by Name.",
            "required": false,
            "type": "string"
          },
          {
            "name": "full",
            "in": "query",
            "description": "Return the full company object with custom data fields and employees. It is recommended to only use this option when filtering by keyword or update timeframe. Default is false.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'Name'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Company"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Companies"
        ],
        "summary": "Create a new Company",
        "description": "Creates new Company defined by a complete Company object.",
        "operationId": "Companies_PostCompany",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "company",
            "in": "body",
            "description": "Complete Company. All fields provided. 'companyId' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Company"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Company"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Companies/{companyId}": {
      "get": {
        "tags": [
          "Companies"
        ],
        "summary": "Get Company",
        "description": "Get single Company by CompanyId",
        "operationId": "Companies_GetCompany",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "companyId",
            "in": "path",
            "description": "Id of Company",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Company"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "Companies"
        ],
        "summary": "Update Company (Complete)",
        "description": "Update Company by CompanyId and complete Company object.",
        "operationId": "Companies_PutCompany",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "companyId",
            "in": "path",
            "description": "Id of Company to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "company",
            "in": "body",
            "description": "Complete Company. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Company"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Company"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Companies"
        ],
        "summary": "Delete Company",
        "description": "Delete single Company by CompanyId",
        "operationId": "Companies_DeleteCompany",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "companyId",
            "in": "path",
            "description": "Id of Company",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "Companies"
        ],
        "summary": "Update Company (Partial)",
        "description": "Update Company by CompanyId and specific changes defined in the JsonPatchDocument.<br />\r\n            Patch example: [{ \"op\": \"replace\", \"path\": \"/name\", \"value\": \"Acme, Inc.\" }]<br />\r\n            Supported fields: email, name",
        "operationId": "Companies_PatchCompany",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "companyId",
            "in": "path",
            "description": "Id of Company to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "companyPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to Company",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[Company]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Company"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Credits": {
      "get": {
        "tags": [
          "Credits"
        ],
        "summary": "Get All Credits for a Product.",
        "description": "Get all Credits for a Product.",
        "operationId": "Credits_GetByProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product for which to get Credits.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'order'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Credit"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Credits"
        ],
        "summary": "Create a new Credit for a Product",
        "description": "Creates new Credit defined by a complete Credit object.",
        "operationId": "Credits_Post",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to which to add the new Credit.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "credit",
            "in": "body",
            "description": "Complete Credit. All fields provided. 'creditId' and 'order' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Credit"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Credit"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Credits/{creditId}": {
      "get": {
        "tags": [
          "Credits"
        ],
        "summary": "Get Credit",
        "description": "Get single Credit by CreditId",
        "operationId": "Credits_Get",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditId",
            "in": "path",
            "description": "Id of Credit",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "productId",
            "in": "query",
            "description": "Id of Product",
            "required": false,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Credit"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "Credits"
        ],
        "summary": "Update Credit (Complete)",
        "description": "Update Credit by CreditId and complete Credit object.",
        "operationId": "Credits_Put",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditId",
            "in": "path",
            "description": "Id of Credit to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "credit",
            "in": "body",
            "description": "Complete Credit. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Credit"
            }
          },
          {
            "name": "productId",
            "in": "query",
            "description": "Id of Product",
            "required": false,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Credit"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Credits"
        ],
        "summary": "Delete Credit",
        "description": "Delete single Credit by CreditId",
        "operationId": "Credits_Delete",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditId",
            "in": "path",
            "description": "Id of Credit",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "productId",
            "in": "query",
            "description": "Id of Product",
            "required": false,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "Credits"
        ],
        "summary": "Update Credit (Partial)",
        "description": "Update Credit by CreditId and specific changes defined in the JsonPatchDocument. Patch example: [{ \"op\": \"replace\", \"path\": \"/amount\", \"value\": \"Some New Amount\" }]",
        "operationId": "Credits_Patch",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditId",
            "in": "path",
            "description": "Id of Credit to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "creditPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to Credit",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[Credit]"
            }
          },
          {
            "name": "productId",
            "in": "query",
            "description": "Id of Product",
            "required": false,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Credit"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/CreditTypes": {
      "get": {
        "tags": [
          "CreditTypes"
        ],
        "summary": "Get All CreditTypes",
        "description": "Get all CreditTypes for tenant.",
        "operationId": "CreditTypes_GetAllCreditTypes",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'order'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/CreditType"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "CreditTypes"
        ],
        "summary": "Create a new CreditType",
        "description": "Creates new CreditType defined by a complete CreditType object.",
        "operationId": "CreditTypes_PostCreditType",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditType",
            "in": "body",
            "description": "Complete CreditType. All fields provided. 'creditTypeId' and 'order' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/CreditType"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/CreditType"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/CreditTypes/{creditTypeId}": {
      "get": {
        "tags": [
          "CreditTypes"
        ],
        "summary": "Get CreditType",
        "description": "Get single CreditType by CreditTypeId",
        "operationId": "CreditTypes_GetCreditType",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditTypeId",
            "in": "path",
            "description": "Id of CreditType",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CreditType"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "CreditTypes"
        ],
        "summary": "Update CreditType (Complete)",
        "description": "Update CreditType by CreditTypeId and complete CreditType object.",
        "operationId": "CreditTypes_PutCreditType",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditTypeId",
            "in": "path",
            "description": "Id of CreditType to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "creditType",
            "in": "body",
            "description": "Complete CreditType. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/CreditType"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CreditType"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "CreditTypes"
        ],
        "summary": "Delete CreditType",
        "description": "Delete single CreditType by CreditTypeId",
        "operationId": "CreditTypes_DeleteCreditType",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditTypeId",
            "in": "path",
            "description": "Id of CreditType",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "CreditTypes"
        ],
        "summary": "Update CreditType (Partial)",
        "description": "Update CreditType by CreditTypeId and specific changes defined in the JsonPatchDocument. Patch example: [{ \"op\": \"replace\", \"path\": \"/label\", \"value\": \"Some New Label\" }]",
        "operationId": "CreditTypes_PatchCreditType",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditTypeId",
            "in": "path",
            "description": "Id of CreditType to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "creditTypePatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to CreditType",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[CreditType]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CreditType"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/CustomDatas/{customDataId}": {
      "get": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Get CustomData",
        "description": "Get single CustomData by CustomDataId",
        "operationId": "CustomDatas_Get",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataId",
            "in": "path",
            "description": "Id of CustomData",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Update CustomData (Complete)",
        "description": "Update CustomData by CustomDataId and complete CustomData object.",
        "operationId": "CustomDatas_Put",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataId",
            "in": "path",
            "description": "Id of CustomData to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customData",
            "in": "body",
            "description": "Complete CustomData. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Delete CustomData",
        "description": "Delete single CustomData by CustomDataId",
        "operationId": "CustomDatas_Delete",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataId",
            "in": "path",
            "description": "Id of CustomData",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Update CustomData (Partial)",
        "description": "Update CustomData (Data, IsPlainText, CustomDataFieldId) by CustomDataId and specific changes defined in the JsonPatchDocument. Patch example: [{ \"op\": \"replace\", \"path\": \"/data\", \"value\": \"Some new data\" }]",
        "operationId": "CustomDatas_Patch",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataId",
            "in": "path",
            "description": "Id of CustomData to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customDataPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to CustomData",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[CustomData]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/CustomDatas": {
      "get": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Get All CustomDatas by Product",
        "description": "Get all CustomDatas for a product.",
        "operationId": "CustomDatas_GetByProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of Product",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/CustomData"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Credits/{creditId}/CustomDatas": {
      "get": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Get All CustomDatas by Credit",
        "description": "Get all CustomDatas for a credit.",
        "operationId": "CustomDatas_GetByCredit",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditId",
            "in": "path",
            "description": "Id of Credit",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/CustomData"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Create a new CustomData for Credit",
        "description": "Creates new CustomData for a Credit defined by a complete CustomData object.",
        "operationId": "CustomDatas_PostByCredit",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "creditId",
            "in": "path",
            "description": "Credit to which to add the CustomData.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customData",
            "in": "body",
            "description": "Complete CustomData. All fields provided. 'customDataId' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Credits/{productId}/CustomDatas": {
      "post": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Create a new CustomData for Product",
        "description": "Creates new CustomData for a Product defined by a complete CustomData object.",
        "operationId": "CustomDatas_PostByProduct",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to which to add the CustomData.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customData",
            "in": "body",
            "description": "Complete CustomData. All fields provided. 'customDataId' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/CustomData"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/CustomDataFields": {
      "get": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Get All CustomDataFields",
        "description": "Get all CustomDataFields for tenant.",
        "operationId": "CustomDatas_GetAllCustomDataFields",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'order'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/CustomDataField"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Create a new CustomDataField",
        "description": "Creates new CustomDataField defined by a complete CustomDataField object.",
        "operationId": "CustomDatas_PostCustomDataField",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataField",
            "in": "body",
            "description": "Complete CustomDataField. All fields provided. 'customDataFieldId' and 'order' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/CustomDataField"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/CustomDataField"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/CustomDataFields/{customDataFieldId}": {
      "get": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Get CustomDataField",
        "description": "Get single CustomDataField by CustomDataFieldId",
        "operationId": "CustomDatas_GetCustomDataField",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataFieldId",
            "in": "path",
            "description": "Id of CustomDataField",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CustomDataField"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Update CustomDataField (Complete)",
        "description": "Update CustomDataField by CustomDataFieldId and complete CustomDataField object.",
        "operationId": "CustomDatas_PutCustomDataField",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataFieldId",
            "in": "path",
            "description": "Id of CustomDataField to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customDataField",
            "in": "body",
            "description": "Complete CustomDataField. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/CustomDataField"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CustomDataField"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Delete CustomDataField",
        "description": "Delete single CustomDataField by CustomDataFieldId",
        "operationId": "CustomDatas_DeleteCustomDataField",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataFieldId",
            "in": "path",
            "description": "Id of CustomDataField",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "CustomDatas (Products)"
        ],
        "summary": "Update CustomDataField (Partial)",
        "description": "Update CustomDataField by CustomDataFieldId and specific changes defined in the JsonPatchDocument. Patch example: [{ \"op\": \"replace\", \"path\": \"/label\", \"value\": \"Some New Label\" }]",
        "operationId": "CustomDatas_PatchCustomDataField",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customDataFieldId",
            "in": "path",
            "description": "Id of CustomDataField to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customDataFieldPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to CustomDataField",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[CustomDataField]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/CustomDataField"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers": {
      "get": {
        "tags": [
          "Customers"
        ],
        "summary": "Get All Customers by Search",
        "description": "Get all Customers for tenant.",
        "operationId": "Customers_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "fromDate",
            "in": "query",
            "description": "Search records updated since the fromDate. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "toDate",
            "in": "query",
            "description": "Search records updated before the toDate. This is used with fromDate to choose a range. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "keyword",
            "in": "query",
            "description": "Search by Name, Email, Phone and Company.",
            "required": false,
            "type": "string"
          },
          {
            "name": "full",
            "in": "query",
            "description": "Return the full customer object, group memberships and custom data fields. It is recommended to only use this option when filtering by keyword or update timeframe. Default is false.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "fullcompany",
            "in": "query",
            "description": "Return the full company, group memberships and custom data fields. It is recommended to only use this option when filtering by keyword or update timeframe. Default is false.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'Name'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Customer"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Customers"
        ],
        "summary": "Create a new Customer",
        "description": "Creates new Customer defined by a complete Customer object.",
        "operationId": "Customers_PostCustomer",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customer",
            "in": "body",
            "description": "Complete Customer. All fields provided. 'customerId' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/{customerId}": {
      "get": {
        "tags": [
          "Customers"
        ],
        "summary": "Get Customer",
        "description": "Get single Customer by CustomerId",
        "operationId": "Customers_GetCustomer",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "Customers"
        ],
        "summary": "Update Customer (Complete)",
        "description": "Update Customer by CustomerId and complete Customer object.",
        "operationId": "Customers_PutCustomer",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customer",
            "in": "body",
            "description": "Complete Customer. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Customers"
        ],
        "summary": "Delete Customer",
        "description": "Delete single Customer by CustomerId",
        "operationId": "Customers_DeleteCustomer",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "Customers"
        ],
        "summary": "Update Customer (Partial)",
        "description": "Update Customer by CustomerId and specific changes defined in the JsonPatchDocument.<br />\r\n            Patch example: [{ \"op\": \"replace\", \"path\": \"/sicCode\", \"value\": \"700\" }]<br />\r\n            Supported fields: email, firstName, lastName, sicCode, mobile, officePhone, licenseNumber",
        "operationId": "Customers_PatchCustomer",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "customerPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to Customer",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[Customer]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/External/{externalId}": {
      "get": {
        "tags": [
          "Customers"
        ],
        "summary": "Get External Customer",
        "description": "Get single Customer by Id from coordinated exteral system.",
        "operationId": "Customers_GetCustomerExternal",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "externalId",
            "in": "path",
            "description": "External Id of Customer",
            "required": true,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/Email/{email}": {
      "get": {
        "tags": [
          "Customers"
        ],
        "summary": "Get Customers by Email",
        "description": "Get all Customers by email address.<br />\r\n            NOTE: You must include the trailing <strong>/</strong>.<br />\r\n            Example: https://api.ce21.com/service/Customers/Email/test@ce21.com/<br />\r\n            You can also pass a Base64 encoded email. This would be used if the email has a PLUS (+) character.<br />\r\n            Example: https://api.ce21.com/service/Customers/Email/dGVzdEBjZTIxLmNvbQ==<br /><br />\r\n            The POST /service/Customers/Email method could be used instead of this one. It supports all characters in the email.",
        "operationId": "Customers_GetCustomerEmail",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "email",
            "in": "path",
            "description": "Email of Customers",
            "required": true,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/Email": {
      "post": {
        "tags": [
          "Customers"
        ],
        "summary": "Get Customers by Email",
        "description": "Get all Customers by email address.<br /><strong>Supports emails with a PLUS (+) character.</strong>",
        "operationId": "Customers_GetCustomerEmailBody",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "email",
            "in": "body",
            "description": "Email of Customers",
            "required": true,
            "schema": {
              "type": "string"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/Authenticate": {
      "post": {
        "tags": [
          "Customers"
        ],
        "summary": "Customer Delegated Authentication",
        "description": "Authenticates customer from username/password.",
        "operationId": "Customers_Authenticate",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "credentials",
            "in": "body",
            "description": "Complete Credentials.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Credentials"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Customer"
            }
          }
        }
      }
    },
    "/service/Customers/{customerId}/Password": {
      "put": {
        "tags": [
          "Customers"
        ],
        "summary": "Update Customer Password",
        "description": "Updates the password for given customer.",
        "operationId": "Customers_UpdatePassword",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "password",
            "in": "body",
            "description": "New password.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/PutPassword"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/AuthToken/{customerId}": {
      "get": {
        "tags": [
          "Customers"
        ],
        "summary": "Get Customer Auth Token",
        "description": "Authenticate a user and redirect them to a page in the catalog. This is generally used to redirect to the user’s list of purchases. \r\n            This process consists of 2 steps. First, make this call to acquire an authentication token. Second, pass that token to the system with additional \r\n            information where to redirect.<br /><br />\r\n            This method returns the Auth Token using CustomerId.<br />\r\n            *The token will be valid for 1 hour.<br /><br />\r\n            Redirect Options:<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;item={ProductId}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;viewer={EventTimeId}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;download={EventTimeId}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;return_url={any_url}<br />",
        "operationId": "Customers_GetCustomerAuth",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/AuthToken/External/{externalId}": {
      "get": {
        "tags": [
          "Customers"
        ],
        "summary": "Get External Customer Auth Token",
        "description": "Authenticate a user and redirect them to a page in the catalog. This is generally used to redirect to the user’s list of purchases. \r\n            This process consists of 2 steps. First, make this call to acquire an authentication token. Second, pass that token to the system with additional \r\n            information where to redirect.<br /><br />\r\n            This method returns the Auth Token using an Id from coordinated exteral system.<br />\r\n            *The token will be valid for 1 hour.<br /><br />\r\n            Redirect Options:<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;item={ProductId}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;viewer={EventTimeId}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;download={EventTimeId}<br />\r\n            https://{base_url}/remote/auth_redirect/?auth_token={auth_token}&amp;return_url={any_url}<br />",
        "operationId": "Customers_GetCustomerExternalAuth",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "externalId",
            "in": "path",
            "description": "External Id of Customer",
            "required": true,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/CustomFields": {
      "get": {
        "tags": [
          "Customers"
        ],
        "summary": "Get All Available Customer CustomFields",
        "description": "Get all customFields available for Customers for tenant.",
        "operationId": "Customers_GetAvailableCustomeFields",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/CustomField"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Evaluations/Responses/Completed": {
      "get": {
        "tags": [
          "Evaluations"
        ],
        "summary": "Get All Completed Evaluations by Search",
        "description": "Get all Completed Evaluations for tenant.",
        "operationId": "Evaluations_GetAllCompleted",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "fromDate",
            "in": "query",
            "description": "Search by FromDate. Default is null.",
            "required": true,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "toDate",
            "in": "query",
            "description": "Search by ToDate. Default is null.",
            "required": true,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "byissuedate",
            "in": "query",
            "description": "Search by Completion Date or Issue Date. Default is Issue Date.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'CustomerId'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Evaluation"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Evaluations": {
      "get": {
        "tags": [
          "Evaluations"
        ],
        "summary": "Get All Evaluations by Product ID",
        "description": "Get all Evaluations for a product.",
        "operationId": "Evaluations_GetById",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "ID of Product",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "showall",
            "in": "query",
            "description": "Return all complete and incomplete Evaluations. Default is false (complete only).",
            "required": false,
            "type": "boolean"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Evaluation"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/Sku/{sku}/Evaluations": {
      "get": {
        "tags": [
          "Evaluations"
        ],
        "summary": "Get All Evaluations by Product SKU",
        "description": "Get all Evaluations for a product.",
        "operationId": "Evaluations_GetBySku",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "sku",
            "in": "path",
            "description": "SKU of Product",
            "required": true,
            "type": "string"
          },
          {
            "name": "showall",
            "in": "query",
            "description": "Return all complete and incomplete Evaluations. Default is false (complete only).",
            "required": false,
            "type": "boolean"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Evaluation"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Groups": {
      "get": {
        "tags": [
          "Groups"
        ],
        "summary": "Get All Groups by Search",
        "description": "Get all Groups for tenant.",
        "operationId": "Groups_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "keyword",
            "in": "query",
            "description": "Search by keyword.",
            "required": false,
            "type": "string"
          },
          {
            "name": "groupId",
            "in": "query",
            "description": "Search by groupId. Default is all groups.",
            "required": false,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "typeId",
            "in": "query",
            "description": "Search by typeId. Default is all types.",
            "required": false,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "accessibility",
            "in": "query",
            "description": "Search by accessibility. Default is all accessibilities.",
            "required": false,
            "type": "string",
            "enum": [
              "OpenGroup",
              "ClosedGroupPrivate",
              "ClosedGroupPublic",
              "TenantGroup",
              "MembershipGroup",
              "Invisible",
              "CompanyBasedMembershipGroup",
              "SmartListGroup"
            ]
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'Name'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Group"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Groups/Types": {
      "get": {
        "tags": [
          "Groups"
        ],
        "summary": "Get All Group Types",
        "description": "Get all Group Types for tenant.",
        "operationId": "Groups_GetAllTypes",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/GroupType"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/{customerId}/Memberships": {
      "get": {
        "tags": [
          "Groups"
        ],
        "summary": "Get All Group Memberships by CustomerId",
        "description": "Get all Group Memberships for a customer.",
        "operationId": "Groups_GetByCustomerId",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Membership"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Groups"
        ],
        "summary": "Add a Group Membership to a Customer",
        "description": "Adds an group membership to a customer.",
        "operationId": "Groups_AddGroupMembershipToCustomer",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of the customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "model",
            "in": "body",
            "description": "Contains the group membership to add",
            "required": true,
            "schema": {
              "$ref": "#/definitions/QuickMembership"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Membership"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Companies/{companyId}/Memberships": {
      "get": {
        "tags": [
          "Groups"
        ],
        "summary": "Get All Group Memberships by CompanyId",
        "description": "Get all Group Memberships for a company.",
        "operationId": "Groups_GetByCompanyId",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "companyId",
            "in": "path",
            "description": "Id of Company",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Membership"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Groups/{groupId}/Memberships": {
      "get": {
        "tags": [
          "Groups"
        ],
        "summary": "Get All Group Memberships by GroupId",
        "description": "Get all Group Memberships for a group.",
        "operationId": "Groups_GetByGroupId",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "groupId",
            "in": "path",
            "description": "Id of Group",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Membership"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/{customerId}/Memberships/{groupId}": {
      "delete": {
        "tags": [
          "Groups"
        ],
        "summary": "Remove a Group Membership from a Customer",
        "description": "Remove a group membership from a customer.",
        "operationId": "Groups_RemoveGroupMembershipFromCustomer",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Customer to remove from.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "groupId",
            "in": "path",
            "description": "Group to be removed.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/GuestBookTokens": {
      "get": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Search for tokens by name",
        "description": "Get all GuestBook Tokens containing [name].",
        "operationId": "GuestBookTokens_GetGuestBookTokenByName",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "name",
            "in": "query",
            "description": "Name to search by.",
            "required": true,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/GBToken"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Creates a new GuestBook Token.",
        "description": "Creates a new GuestBook Token.",
        "operationId": "GuestBookTokens_CreateNewGuestBookToken",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "t",
            "in": "body",
            "required": true,
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/GuestBookTokens/{guestBookTokenId}": {
      "get": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Search for tokens by ID",
        "description": "Get the Guestbook token with the corresponding ID.",
        "operationId": "GuestBookTokens_GetGuestBookTokenById",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "guestBookTokenId",
            "in": "path",
            "description": "ID to search by.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Delete a GuestBook Token.",
        "description": "Delete a new GuestBook Token by ID.",
        "operationId": "GuestBookTokens_DeleteGuestBookToken",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "guestBookTokenId",
            "in": "path",
            "description": "ID of the token to delete.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/GuestBookTokens": {
      "get": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Get all tokens for a product",
        "description": "Get all GuestBook Tokens associated with the product [name].",
        "operationId": "GuestBookTokens_GetGuestBookTokensByProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of the product",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/GBToken"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Add a GuestBook token to a Product",
        "description": "Adds an existing GuestBook token to a product.",
        "operationId": "GuestBookTokens_AddGuestBookTokenToProduct",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of the product",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "model",
            "in": "body",
            "description": "Contains the guestBookTokenId and expiration",
            "required": true,
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/GuestBookTokens/{guestBookTokenId}": {
      "put": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Update GuestBookToken Expiration on Product",
        "description": "Update the expiration date for a GuestBook token on a particular product. The only field required in the request body is the new \"Expiration\".",
        "operationId": "GuestBookTokens_UpdateGuestBookTokenExpirationOnProduct",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of the product",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "guestBookTokenId",
            "in": "path",
            "description": "Id of the token to be removed",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "model",
            "in": "body",
            "description": "Contains the new expiration date",
            "required": true,
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "GuestBookTokens"
        ],
        "summary": "Remove a GuestBook token from a product",
        "description": "Remove a GuestBook token from a product. Does not delete the underlying GuestBook token",
        "operationId": "GuestBookTokens_RemoveGuestBookTokenFromProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of the product",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "guestBookTokenId",
            "in": "path",
            "description": "Id of the token to be removed",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/GBToken"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Jurisdictions": {
      "get": {
        "tags": [
          "Jurisdictions"
        ],
        "summary": "Get All Jurisdictions",
        "description": "Get all Jurisdictions for tenant.",
        "operationId": "Jurisdictions_GetAllJurisdictions",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'order'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Jurisdiction"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Jurisdictions"
        ],
        "summary": "Create a new Jurisdiction",
        "description": "Creates new Jurisdiction defined by a complete Jurisdiction object.",
        "operationId": "Jurisdictions_PostJurisdiction",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "jurisdiction",
            "in": "body",
            "description": "Complete Jurisdiction. All fields provided. 'jurisdictionId'.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Jurisdiction"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Jurisdiction"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Jurisdictions/{jurisdictionId}": {
      "get": {
        "tags": [
          "Jurisdictions"
        ],
        "summary": "Get Jurisdiction",
        "description": "Get single Jurisdiction by JurisdictionId",
        "operationId": "Jurisdictions_GetJurisdiction",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "jurisdictionId",
            "in": "path",
            "description": "Id of Jurisdiction",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Jurisdiction"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "Jurisdictions"
        ],
        "summary": "Update Jurisdiction (Complete)",
        "description": "Update Jurisdiction by JurisdictionId and complete Jurisdiction object.",
        "operationId": "Jurisdictions_PutJurisdiction",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "jurisdictionId",
            "in": "path",
            "description": "Id of Jurisdiction to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "jurisdiction",
            "in": "body",
            "description": "Complete Jurisdiction. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Jurisdiction"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Jurisdiction"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Jurisdictions"
        ],
        "summary": "Delete Jurisdiction",
        "description": "Delete single Jurisdiction by JurisdictionId",
        "operationId": "Jurisdictions_DeleteJurisdiction",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "jurisdictionId",
            "in": "path",
            "description": "Id of Jurisdiction",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "Jurisdictions"
        ],
        "summary": "Update Jurisdiction (Partial)",
        "description": "Update Jurisdiction by JurisdictionId and specific changes defined in the JsonPatchDocument. Patch example: [{ \"op\": \"replace\", \"path\": \"/label\", \"value\": \"Some New Label\" }]",
        "operationId": "Jurisdictions_PatchJurisdiction",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "jurisdictionId",
            "in": "path",
            "description": "Id of Jurisdiction to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "jurisdictionPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to Jurisdiction",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[Jurisdiction]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Jurisdiction"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Orders": {
      "get": {
        "tags": [
          "Orders"
        ],
        "summary": "Get All Orders by Search",
        "description": "Get all Orders for tenant.",
        "operationId": "Orders_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "fromDate",
            "in": "query",
            "description": "Search orders since the fromDate. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "toDate",
            "in": "query",
            "description": "Search orders before the toDate. This is used with fromDate to choose a range. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'LastModifiedDate'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Order"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Orders"
        ],
        "summary": "Create a new Order",
        "description": "Creates new Order defined by a QuickOrder object.",
        "operationId": "Orders_PostQuickOrder",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "order",
            "in": "body",
            "description": "QuickOrder object.\r\n            Required Fields: \r\n              customerId or externalId\r\n              eventTimeId or sku",
            "required": true,
            "schema": {
              "$ref": "#/definitions/QuickOrder"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Order"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Orders/{orderId}": {
      "get": {
        "tags": [
          "Orders"
        ],
        "summary": "Get Order",
        "description": "Get single Order by OrderId",
        "operationId": "Orders_GetOrder",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "orderId",
            "in": "path",
            "description": "Id of Order",
            "required": true,
            "type": "integer",
            "format": "int64"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Order"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Orders"
        ],
        "summary": "Cancel Order (Full)",
        "description": "Cancel the entire order with all of its registrants.\r\n            It will show in CE21 as being refunded. This method can only be used to cancel\r\n            orders that where made using the Orders POST method of this API.\r\n            \"-Refunded\" will be appended to the end of ExternalOrderId.",
        "operationId": "Orders_Delete",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "orderId",
            "in": "path",
            "description": "Id of Order to cancel.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content (Order Cancelled)",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "Orders"
        ],
        "summary": "Update Order (Partial)",
        "description": "Update Order by OrderId and specific changes defined in the JsonPatchDocument.<br />\r\n            Patch example: [{ \"op\": \"replace\", \"path\": \"/marketingCode\", \"value\": \"BDIETWT\" }]<br />\r\n            Supported fields: marketingCode, paymentStatus, externalOrderId",
        "operationId": "Orders_Patch",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "orderId",
            "in": "path",
            "description": "Id of Order to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "orderPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to Order",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[Order]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Order"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Orders/External/{externalOrderId}": {
      "get": {
        "tags": [
          "Orders"
        ],
        "summary": "Get External Order",
        "description": "Get single Order by Id from coordinated exteral system.",
        "operationId": "Orders_GetOrderExternal",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "externalOrderId",
            "in": "path",
            "description": "External Id of Order",
            "required": true,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Order"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/PriceAdjustments": {
      "get": {
        "tags": [
          "PriceAdjustments"
        ],
        "summary": "Get All PriceAdjustments for a Product.",
        "description": "Get all PriceAdjustments for a Product.",
        "operationId": "PriceAdjustments_GetByProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product for which to get PriceAdjustments.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'name'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/PriceAdjustment"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "PriceAdjustments"
        ],
        "summary": "Create a new PriceAdjustment for a Product",
        "description": "Creates new PriceAdjustment defined by a complete PriceAdjustment object.",
        "operationId": "PriceAdjustments_Post",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to which to add the new PriceAdjustment.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "priceAdjustment",
            "in": "body",
            "description": "Complete PriceAdjustment. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/PriceAdjustment"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/PriceAdjustment"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/PriceAdjustments/FromTemplate": {
      "post": {
        "tags": [
          "PriceAdjustments"
        ],
        "summary": "Create a new PriceAdjustment for a Product from a Template",
        "description": "Creates new PriceAdjustment defined by a template.",
        "operationId": "PriceAdjustments_PostTemplate",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to which to add the new PriceAdjustment.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "templatePriceAdjustment",
            "in": "body",
            "description": "PriceAdjustment Template and details.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/TemplatePriceAdjustment"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/PriceAdjustment"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/PriceAdjustments/{priceAdjustmentId}": {
      "get": {
        "tags": [
          "PriceAdjustments"
        ],
        "summary": "Get PriceAdjustment",
        "description": "Get single PriceAdjustment by PriceAdjustmentId",
        "operationId": "PriceAdjustments_Get",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "priceAdjustmentId",
            "in": "path",
            "description": "Id of PriceAdjustment",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/PriceAdjustment"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "PriceAdjustments"
        ],
        "summary": "Update PriceAdjustment (Complete)",
        "description": "Update PriceAdjustment by PriceAdjustmentId and complete PriceAdjustment object.",
        "operationId": "PriceAdjustments_Put",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "priceAdjustmentId",
            "in": "path",
            "description": "Id of PriceAdjustment to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "priceAdjustment",
            "in": "body",
            "description": "Complete PriceAdjustment. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/PriceAdjustment"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/PriceAdjustment"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "PriceAdjustments"
        ],
        "summary": "Delete PriceAdjustment",
        "description": "Delete single PriceAdjustment by PriceAdjustmentId",
        "operationId": "PriceAdjustments_Delete",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "priceAdjustmentId",
            "in": "path",
            "description": "Id of PriceAdjustment",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "PriceAdjustments"
        ],
        "summary": "Update PriceAdjustment (Partial)",
        "description": "Update PriceAdjustment by PriceAdjustmentId and specific changes defined in the JsonPatchDocument. Patch example: [{ \"op\": \"replace\", \"path\": \"/setPrice\", \"value\": \"99.99\" }]",
        "operationId": "PriceAdjustments_Patch",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "priceAdjustmentId",
            "in": "path",
            "description": "Id of PriceAdjustment to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "priceAdjustmentPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to PriceAdjustment",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[PriceAdjustment]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/PriceAdjustment"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products": {
      "get": {
        "tags": [
          "Products"
        ],
        "summary": "Get All Products by Search",
        "description": "Get all Products for tenant. For a more comprehensive representation on the available programs in the catalog, use the product feeds. https://manager.ce21.com/Setting/ApiSettings#ProductFeeds",
        "operationId": "Products_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productTypeId",
            "in": "query",
            "description": "Search by ProductTypeId. Default is 0.",
            "required": false,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "categoryId",
            "in": "query",
            "description": "Search by CategoryId. Default is 0.",
            "required": false,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "tagId",
            "in": "query",
            "description": "Search by TagId. Default is 0.",
            "required": false,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "showAll",
            "in": "query",
            "description": "Show all products including inactive. Default is false.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "fromDate",
            "in": "query",
            "description": "Search by FromDate. Default is null. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "toDate",
            "in": "query",
            "description": "Search by ToDate. Default is null. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'ProductId'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Product"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Products"
        ],
        "summary": "Create a new Product",
        "description": "Creates new Product defined by a QuickProduct object. \r\n            Live type products require StartDateTime and EndDateTime (dates are UTC). \r\n            Non-live types require an OriginalDate and Duration.",
        "operationId": "Products_PostQuickProduct",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "product",
            "in": "body",
            "description": "QuickProduct",
            "required": true,
            "schema": {
              "$ref": "#/definitions/QuickProduct"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Product"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/ParentProducts/{parentProductId}/Products": {
      "get": {
        "tags": [
          "Products"
        ],
        "summary": "Get Products by ParentProductId",
        "description": "Get all products for for a given product family.",
        "operationId": "Products_GetByParentProductId",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "parentProductId",
            "in": "path",
            "description": "Search by ParentProductId.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'ProductId'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Product"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}": {
      "get": {
        "tags": [
          "Products"
        ],
        "summary": "Get Product",
        "description": "Get single Product by ProductId",
        "operationId": "Products_GetById",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of Product to get.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Product"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "Products"
        ],
        "summary": "Update Product (Complete)",
        "description": "Update Product by ProductId and complete Product object.<br />\r\n            Live type products require StartDateTime and EndDateTime (dates are UTC). \r\n            Non-live types require an OriginalDate and Duration.",
        "operationId": "Products_PutProduct",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of Product to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "product",
            "in": "body",
            "description": "Complete Product. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Product"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Product"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Products"
        ],
        "summary": "Delete Product",
        "description": "Delete single Product by ProductId",
        "operationId": "Products_Delete",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of Product to delete.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "Products"
        ],
        "summary": "Update Product (Partial)",
        "description": "Update Product by ProductId and specific changes defined in the JsonPatchDocument.<br />\r\n            Patch example: [{ \"op\": \"replace\", \"path\": \"/name\", \"value\": \"Some New Product Name\" }]<br />\r\n            Live type products require StartDateTime and EndDateTime (dates are UTC). \r\n            Non-live types require an OriginalDate and Duration.",
        "operationId": "Products_PatchProduct",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Id of Product to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "productPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to Product",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[Product]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Product"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/Sku/{sku}": {
      "get": {
        "tags": [
          "Products"
        ],
        "summary": "Get Product",
        "description": "Get single Product by ProductId",
        "operationId": "Products_GetBySku",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "sku",
            "in": "path",
            "description": "SKU of Product to get.",
            "required": true,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Product"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/CourseLevels": {
      "get": {
        "tags": [
          "Products"
        ],
        "summary": "Get All CourseLevels",
        "description": "Get all CourseLevels for tenant. Use these when creating products.",
        "operationId": "Products_GetAllCourseLevels",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/CourseLevel"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/FromTemplate": {
      "post": {
        "tags": [
          "Products"
        ],
        "summary": "Create a new Products from Template",
        "description": "Creates new products defined by a template.",
        "operationId": "Products_PostTemplateProduct",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "template",
            "in": "body",
            "description": "TemplateProduct",
            "required": true,
            "schema": {
              "$ref": "#/definitions/TemplateProduct"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Product"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Registrations/Completed": {
      "get": {
        "tags": [
          "Registrations"
        ],
        "summary": "Get All Completed Registrations by Search",
        "description": "Get all Completed Registrations for tenant.",
        "operationId": "Registrations_GetAllCompleted",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "fromDate",
            "in": "query",
            "description": "Search by FromDate. Default is null. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": true,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "toDate",
            "in": "query",
            "description": "Search by ToDate. Default is null. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": true,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "byissuedate",
            "in": "query",
            "description": "Search by Completion Date or Issue Date. Default is Issue Date.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "full",
            "in": "query",
            "description": "Return the full registration object with full product and customer fields. It is recommended to only use this option when filtering by a small timeframe. Default is false.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'CustomerId'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Registration"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Registrations": {
      "get": {
        "tags": [
          "Registrations"
        ],
        "summary": "Get All Registrations by Product ID",
        "description": "Get all Registrations for a product.",
        "operationId": "Registrations_GetById",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "ID of Product",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "showall",
            "in": "query",
            "description": "Return all complete and incomplete registrations. Default is false (complete only).",
            "required": false,
            "type": "boolean"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Registration"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Registrations/{registrationId}": {
      "get": {
        "tags": [
          "Registrations"
        ],
        "summary": "Get Registration",
        "description": "Get single Registration by RegistrationId",
        "operationId": "Registrations_GetById",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "registrationId",
            "in": "path",
            "description": "Id of Registration to get.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Registration"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Registrations"
        ],
        "summary": "Deactivate Registration",
        "description": "Deactivate a single registration. It will show in CE21 as deactivated.\r\n            This method can be used for APi an CE21 Catalog registrations.",
        "operationId": "Registrations_Delete",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "registrationId",
            "in": "path",
            "description": "Id of Registration to deactivate.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/Sku/{sku}/Registrations": {
      "get": {
        "tags": [
          "Registrations"
        ],
        "summary": "Get All Registrations by Product SKU",
        "description": "Get all Registrations for a product.",
        "operationId": "Registrations_GetBySku",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "sku",
            "in": "path",
            "description": "SKU of Product",
            "required": true,
            "type": "string"
          },
          {
            "name": "showall",
            "in": "query",
            "description": "Return all complete and incomplete registrations. Default is false (complete only).",
            "required": false,
            "type": "boolean"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Registration"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/{customerId}/Registrations": {
      "get": {
        "tags": [
          "Registrations"
        ],
        "summary": "Get All Registrations by CustomerId",
        "description": "Get all Registrations for a customer.",
        "operationId": "Registrations_GetByCustomerId",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "showall",
            "in": "query",
            "description": "Return all complete and incomplete registrations. Default is false (complete only).",
            "required": false,
            "type": "boolean"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Registration"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/External/{externalId}/Registrations": {
      "get": {
        "tags": [
          "Registrations"
        ],
        "summary": "Get All Registrations by ExternalId",
        "description": "Get all Registrations for a customer.",
        "operationId": "Registrations_GetByExternalId",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "externalId",
            "in": "path",
            "description": "ExternalId of Customer",
            "required": true,
            "type": "string"
          },
          {
            "name": "showall",
            "in": "query",
            "description": "Return all complete and incomplete registrations. Default is false (complete only).",
            "required": false,
            "type": "boolean"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Registration"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Speakers": {
      "get": {
        "tags": [
          "Speakers"
        ],
        "summary": "Get All Speakers by Search",
        "description": "Get all Speakers for tenant.",
        "operationId": "Speakers_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "fromDate",
            "in": "query",
            "description": "Search records updated since the fromDate. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "toDate",
            "in": "query",
            "description": "Search records updated before the toDate. This is used with fromDate to choose a range. The date must be in the ISO 8601 UTC format. (2016-01-01T00:00:00Z)",
            "required": false,
            "type": "string",
            "format": "date-time"
          },
          {
            "name": "keyword",
            "in": "query",
            "description": "Search by Name, Email, Phone and Company.",
            "required": false,
            "type": "string"
          },
          {
            "name": "full",
            "in": "query",
            "description": "Return the full speaker object with full company and custom data fields. It is recommended to only use this option when filtering by keyword or update timeframe. Default is false.",
            "required": false,
            "type": "boolean"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'Name'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Speaker"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "post": {
        "tags": [
          "Speakers"
        ],
        "summary": "Create a new Speaker",
        "description": "Creates new Speaker defined by a complete Speaker object.<br />\r\n            If you try to create a speaker using an existing customer (defined by SpeakerId or ExternalId),\r\n            the customer will be upgraded to a speaker and updated defined by the rest of the speaker object.",
        "operationId": "Speakers_PostSpeaker",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "speaker",
            "in": "body",
            "description": "Complete Speaker. All fields provided. 'speakerId' to be 0.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Speakers/{speakerId}": {
      "get": {
        "tags": [
          "Speakers"
        ],
        "summary": "Get Speaker",
        "description": "Get single Speaker by SpeakerId",
        "operationId": "Speakers_GetSpeaker",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "speakerId",
            "in": "path",
            "description": "Id of Speaker",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "put": {
        "tags": [
          "Speakers"
        ],
        "summary": "Update Speaker (Complete)",
        "description": "Update Speaker by SpeakerId and complete Speaker object.",
        "operationId": "Speakers_PutSpeaker",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "speakerId",
            "in": "path",
            "description": "Id of Speaker to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "speaker",
            "in": "body",
            "description": "Complete Speaker. All fields provided.",
            "required": true,
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Speakers"
        ],
        "summary": "Delete Speaker",
        "description": "Delete single Speaker by SpeakerId",
        "operationId": "Speakers_DeleteSpeaker",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "speakerId",
            "in": "path",
            "description": "Id of Speaker",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "patch": {
        "tags": [
          "Speakers"
        ],
        "summary": "Update Speaker (Partial)",
        "description": "Update Speaker by SpeakerId and specific changes defined in the JsonPatchDocument.<br />\r\n            Patch example: [{ \"op\": \"replace\", \"path\": \"/sicCode\", \"value\": \"700\" }]<br />\r\n            Supported fields: email, firstName, lastName, sicCode, mobile, officePhone, licenseNumber",
        "operationId": "Speakers_PatchSpeaker",
        "consumes": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml",
          "application/x-www-form-urlencoded"
        ],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "speakerId",
            "in": "path",
            "description": "Id of Speaker to update.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "speakerPatchDocument",
            "in": "body",
            "description": "JsonPatchDocument with changes to Speaker",
            "required": true,
            "schema": {
              "$ref": "#/definitions/JsonPatchDocument[Speaker]"
            }
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Speakers/External/{externalId}": {
      "get": {
        "tags": [
          "Speakers"
        ],
        "summary": "Get External Speaker",
        "description": "Get single Speaker by Id from coordinated exteral system.",
        "operationId": "Speakers_GetSpeakerExternal",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "externalId",
            "in": "path",
            "description": "External Id of Speaker",
            "required": true,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Speakers": {
      "get": {
        "tags": [
          "Speakers"
        ],
        "summary": "Get All Speakers by Product ID",
        "description": "Get all speakers for a product.",
        "operationId": "Speakers_GetSpeakersByProductId",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "ID of Product",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Speaker"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Speakers/{speakerId}": {
      "post": {
        "tags": [
          "Speakers"
        ],
        "summary": "Add a Speaker to a Product",
        "description": "Add a speaker to a product using their IDs. Returns the new complete list of speakers for the product.",
        "operationId": "Speakers_PostSpeakerToProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to be related.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "speakerId",
            "in": "path",
            "description": "Speaker to add to the Product.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Speakers"
        ],
        "summary": "Remove Speaker from Product",
        "description": "Remove single Speaker from a Product",
        "operationId": "Speakers_RemoveSpeakerFromProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to remove from.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "speakerId",
            "in": "path",
            "description": "Speaker to be removed.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Customers/{customerId}/ToSpeaker": {
      "patch": {
        "tags": [
          "Speakers"
        ],
        "summary": "Update Customer to Speaker",
        "description": "Updates the customer to be a speaker.",
        "operationId": "Speakers_UpdateToSpeaker",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "customerId",
            "in": "path",
            "description": "Id of Customer",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Speaker"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Venues": {
      "get": {
        "tags": [
          "Venues"
        ],
        "summary": "Get All Venues for Tenant",
        "operationId": "Venues_GetAll",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "type",
            "in": "query",
            "description": "Type of venues. (Public or Private). Default is 'Public'.",
            "required": false,
            "type": "string",
            "enum": [
              "Public",
              "Private"
            ]
          },
          {
            "name": "keyword",
            "in": "query",
            "description": "Search by Name/Address.",
            "required": false,
            "type": "string"
          },
          {
            "name": "country",
            "in": "query",
            "description": "Get all venues in country.",
            "required": false,
            "type": "string"
          },
          {
            "name": "state",
            "in": "query",
            "description": "Get all venues in state.",
            "required": false,
            "type": "string"
          },
          {
            "name": "city",
            "in": "query",
            "description": "Get all venues in city.",
            "required": false,
            "type": "string"
          },
          {
            "name": "sort",
            "in": "query",
            "description": "Field to use for sorting the results. Default is 'Name'.",
            "required": false,
            "type": "string"
          },
          {
            "name": "fields",
            "in": "query",
            "description": "Comma delimited list of fields to be returned. Default is all.",
            "required": false,
            "type": "string"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Venue"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Venues/{venueId}": {
      "get": {
        "tags": [
          "Venues"
        ],
        "summary": "Get Venue",
        "description": "Get single venue.",
        "operationId": "Venues_GetVenue",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "venueId",
            "in": "path",
            "description": "Id of Venue",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "$ref": "#/definitions/Venue"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Venues": {
      "get": {
        "tags": [
          "Venues"
        ],
        "summary": "Get Venue for a Product",
        "description": "Get venue for a product.",
        "operationId": "Venues_GetProductVenues",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product Id",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "200": {
            "description": "Ok",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Venue"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    },
    "/service/Products/{productId}/Venues/{venueId}": {
      "post": {
        "tags": [
          "Venues"
        ],
        "summary": "Add a Venue to a Product",
        "description": "Adds a venue to a product. Only one venue can be added to a product.",
        "operationId": "Venues_PostVenueToProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to be related.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "venueId",
            "in": "path",
            "description": "Venue to add to the Product.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "201": {
            "description": "Created",
            "schema": {
              "type": "array",
              "items": {
                "$ref": "#/definitions/Venue"
              }
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      },
      "delete": {
        "tags": [
          "Venues"
        ],
        "summary": "Remove Venue from Product",
        "description": "Remove single Venue from a Product",
        "operationId": "Venues_RemoveVenueFromProduct",
        "consumes": [],
        "produces": [
          "application/json",
          "text/json",
          "text/html",
          "application/json-patch+json",
          "application/xml",
          "text/xml"
        ],
        "parameters": [
          {
            "name": "productId",
            "in": "path",
            "description": "Product to remove from.",
            "required": true,
            "type": "integer",
            "format": "int32"
          },
          {
            "name": "venueId",
            "in": "path",
            "description": "Venue to be removed.",
            "required": true,
            "type": "integer",
            "format": "int32"
          }
        ],
        "responses": {
          "204": {
            "description": "No Content",
            "schema": {
              "type": "object"
            }
          },
          "400": {
            "description": "Bad Request"
          },
          "404": {
            "description": "Not found"
          },
          "500": {
            "description": "Internal Server Error"
          }
        }
      }
    }
  },
  "definitions": {
    "Category": {
      "type": "object",
      "properties": {
        "categoryId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "slug": {
          "type": "string"
        },
        "description": {
          "type": "string"
        },
        "parentId": {
          "format": "int32",
          "type": "integer"
        },
        "isDelete": {
          "type": "boolean"
        },
        "title": {
          "type": "string"
        },
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "parentCategory": {
          "type": "string"
        }
      }
    },
    "Company": {
      "required": [
        "accountType"
      ],
      "type": "object",
      "properties": {
        "companyId": {
          "format": "int32",
          "type": "integer"
        },
        "accountType": {
          "enum": [
            "Customer",
            "Vendor"
          ],
          "type": "string"
        },
        "name": {
          "type": "string"
        },
        "sic": {
          "type": "string"
        },
        "email": {
          "type": "string"
        },
        "domains": {
          "type": "string"
        },
        "address": {
          "$ref": "#/definitions/Address"
        },
        "mobile": {
          "type": "string"
        },
        "officePhone": {
          "type": "string"
        },
        "otherPhone": {
          "type": "string"
        },
        "fax": {
          "type": "string"
        },
        "website": {
          "type": "string"
        },
        "blog": {
          "type": "string"
        },
        "description": {
          "type": "string"
        },
        "youtube": {
          "type": "string"
        },
        "facebook": {
          "type": "string"
        },
        "twitter": {
          "type": "string"
        },
        "linkedIn": {
          "type": "string"
        },
        "instagram": {
          "type": "string"
        },
        "image": {
          "$ref": "#/definitions/Image"
        },
        "customFields": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/CustomField"
          }
        },
        "employees": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Customer"
          }
        }
      }
    },
    "Address": {
      "type": "object",
      "properties": {
        "addressId": {
          "format": "int32",
          "type": "integer"
        },
        "addressLine1": {
          "type": "string"
        },
        "addressLine2": {
          "type": "string"
        },
        "city": {
          "type": "string"
        },
        "state": {
          "type": "string"
        },
        "postalCode": {
          "type": "string"
        },
        "county": {
          "type": "string"
        },
        "country": {
          "type": "string"
        }
      }
    },
    "Image": {
      "type": "object",
      "properties": {
        "url": {
          "type": "string"
        },
        "title": {
          "type": "string"
        },
        "alt": {
          "type": "string"
        }
      }
    },
    "CustomField": {
      "required": [
        "choice",
        "fieldType"
      ],
      "type": "object",
      "properties": {
        "fieldId": {
          "format": "int32",
          "type": "integer"
        },
        "field": {
          "type": "string"
        },
        "value": {
          "type": "string"
        },
        "choice": {
          "enum": [
            "Open",
            "Single",
            "Multi",
            "Date"
          ],
          "type": "string"
        },
        "fieldType": {
          "enum": [
            "MultiChoiceSingleAnswerRadioButton",
            "MultiChoiceMultiAnswer",
            "Text",
            "MultiChoiceSingleAnswerDropDown",
            "Date",
            "Country",
            "State",
            "Number",
            "AcceptQuestion",
            "AddressBlock"
          ],
          "type": "string"
        },
        "options": {
          "type": "object"
        },
        "note": {
          "type": "string"
        }
      }
    },
    "Customer": {
      "type": "object",
      "properties": {
        "customerId": {
          "format": "int32",
          "type": "integer"
        },
        "externalId": {
          "type": "string"
        },
        "email": {
          "type": "string"
        },
        "prefix": {
          "type": "string"
        },
        "firstName": {
          "type": "string"
        },
        "middleName": {
          "type": "string"
        },
        "lastName": {
          "type": "string"
        },
        "suffix": {
          "type": "string"
        },
        "credential": {
          "type": "string"
        },
        "jobTitle": {
          "type": "string"
        },
        "companyName": {
          "type": "string"
        },
        "companyId": {
          "format": "int32",
          "type": "integer"
        },
        "company": {
          "$ref": "#/definitions/Company"
        },
        "sicCode": {
          "type": "string"
        },
        "mobile": {
          "type": "string"
        },
        "officePhone": {
          "type": "string"
        },
        "licenseNumber": {
          "type": "string"
        },
        "image": {
          "$ref": "#/definitions/Image"
        },
        "address": {
          "$ref": "#/definitions/Address"
        },
        "customFields": {
          "description": "Address Block not supported in API",
          "type": "array",
          "items": {
            "$ref": "#/definitions/CustomField"
          }
        }
      }
    },
    "Membership": {
      "type": "object",
      "properties": {
        "membershipId": {
          "format": "int32",
          "type": "integer"
        },
        "groupId": {
          "format": "int32",
          "type": "integer"
        },
        "customerId": {
          "format": "int32",
          "type": "integer"
        },
        "companyId": {
          "format": "int32",
          "type": "integer"
        },
        "status": {
          "enum": [
            "PendingApproval",
            "Active",
            "Lapsed",
            "PendigPayment",
            "PendingLevelChange",
            "Suspended",
            "Reject",
            "Invited",
            "Requested",
            "Expired",
            "PendingRequirement",
            "PendingRenewalApproval",
            "UserRejected",
            "Renewed"
          ],
          "type": "string"
        },
        "currentStartDate": {
          "format": "date-time",
          "type": "string"
        },
        "currentEndDate": {
          "format": "date-time",
          "type": "string"
        },
        "nextRenewalDue": {
          "format": "date-time",
          "type": "string"
        },
        "endDate": {
          "format": "date-time",
          "type": "string"
        },
        "changeGroupTo": {
          "type": "string"
        },
        "changeStatusTo": {
          "type": "string"
        },
        "fee": {
          "format": "double",
          "type": "number"
        },
        "tax": {
          "format": "double",
          "type": "number"
        },
        "paymentStatus": {
          "enum": [
            "Active",
            "PaymentDue",
            "PaymentFailed"
          ],
          "type": "string"
        },
        "billingCycle": {
          "enum": [
            "Yearly",
            "BiYearly",
            "Quarterly",
            "BiMonthly",
            "Monthly",
            "PayAllYears"
          ],
          "type": "string"
        },
        "memberSince": {
          "format": "date-time",
          "type": "string"
        },
        "memberNumber": {
          "type": "string"
        },
        "owner": {
          "type": "string"
        },
        "numberOfEmployees": {
          "format": "int32",
          "type": "integer"
        },
        "parentMembershipId": {
          "format": "int32",
          "type": "integer"
        },
        "group": {
          "$ref": "#/definitions/Group"
        },
        "customer": {
          "$ref": "#/definitions/Customer"
        }
      }
    },
    "Group": {
      "type": "object",
      "properties": {
        "groupId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "public": {
          "type": "boolean"
        },
        "hidden": {
          "type": "boolean"
        },
        "fee": {
          "format": "double",
          "type": "number"
        },
        "createdDate": {
          "format": "date-time",
          "type": "string"
        },
        "accessibility": {
          "enum": [
            "OpenGroup",
            "ClosedGroupPrivate",
            "ClosedGroupPublic",
            "TenantGroup",
            "MembershipGroup",
            "Invisible",
            "CompanyBasedMembershipGroup",
            "SmartListGroup"
          ],
          "type": "string"
        },
        "renewalPeriod": {
          "enum": [
            "Never",
            "Monthly",
            "EveryYear",
            "EveryTwoYear",
            "EveryThreeYear",
            "EveryFourYear",
            "EveryFiveYear",
            "ExpireAfterOneYear",
            "ExpireAfterTwoYear",
            "ExpireAfterThreeYear",
            "ExpireAfterFourYear",
            "ExpireAfterFiveYear",
            "AllowMemberToSelect"
          ],
          "type": "string",
          "readOnly": true
        },
        "type": {
          "$ref": "#/definitions/GroupType"
        }
      }
    },
    "GroupType": {
      "type": "object",
      "properties": {
        "typeId": {
          "format": "int32",
          "type": "integer"
        },
        "label": {
          "type": "string"
        }
      }
    },
    "JsonPatchDocument[Company]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[Company]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[Company]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "Credit": {
      "type": "object",
      "properties": {
        "creditId": {
          "format": "int32",
          "type": "integer"
        },
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "amount": {
          "type": "string"
        },
        "order": {
          "format": "int32",
          "type": "integer"
        },
        "startDate": {
          "format": "date-time",
          "type": "string"
        },
        "endDate": {
          "format": "date-time",
          "type": "string"
        },
        "creditTypeId": {
          "format": "int32",
          "type": "integer"
        },
        "creditType": {
          "$ref": "#/definitions/CreditType"
        }
      }
    },
    "CreditType": {
      "type": "object",
      "properties": {
        "creditTypeId": {
          "format": "int32",
          "type": "integer"
        },
        "label": {
          "type": "string"
        },
        "displayName": {
          "type": "string"
        },
        "order": {
          "format": "int32",
          "type": "integer"
        },
        "creditStatement": {
          "type": "string"
        },
        "marketingStatement": {
          "type": "string"
        },
        "useCreditAsMarketing": {
          "type": "boolean"
        },
        "jurisdictionId": {
          "format": "int32",
          "type": "integer"
        },
        "jurisdiction": {
          "$ref": "#/definitions/Jurisdiction"
        }
      }
    },
    "Jurisdiction": {
      "type": "object",
      "properties": {
        "jurisdictionId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "order": {
          "format": "int32",
          "type": "integer"
        },
        "statement": {
          "type": "string"
        },
        "marketingStatement": {
          "type": "string"
        },
        "useCreditAsMarketing": {
          "type": "boolean"
        },
        "creditTypes": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/CreditType"
          }
        }
      }
    },
    "JsonPatchDocument[Credit]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[Credit]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[Credit]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "JsonPatchDocument[CreditType]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[CreditType]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[CreditType]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "CustomData": {
      "type": "object",
      "properties": {
        "customDataId": {
          "format": "int32",
          "type": "integer"
        },
        "data": {
          "type": "string"
        },
        "isPlainText": {
          "type": "boolean"
        },
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "creditId": {
          "format": "int32",
          "type": "integer"
        },
        "customDataFieldId": {
          "format": "int32",
          "type": "integer"
        },
        "customDataField": {
          "$ref": "#/definitions/CustomDataField"
        }
      }
    },
    "CustomDataField": {
      "type": "object",
      "properties": {
        "customDataFieldId": {
          "format": "int32",
          "type": "integer"
        },
        "label": {
          "type": "string"
        },
        "description": {
          "type": "string"
        },
        "headerLabel": {
          "type": "string"
        },
        "order": {
          "format": "int32",
          "type": "integer"
        }
      }
    },
    "JsonPatchDocument[CustomData]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[CustomData]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[CustomData]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "JsonPatchDocument[CustomDataField]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[CustomDataField]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[CustomDataField]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "JsonPatchDocument[Customer]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[Customer]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[Customer]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "Credentials": {
      "type": "object",
      "properties": {
        "username": {
          "type": "string"
        },
        "password": {
          "type": "string"
        },
        "sourceIp": {
          "type": "string"
        }
      }
    },
    "PutPassword": {
      "required": [
        "password"
      ],
      "type": "object",
      "properties": {
        "password": {
          "type": "string"
        }
      }
    },
    "Evaluation": {
      "type": "object",
      "properties": {
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "productSku": {
          "type": "string"
        },
        "productName": {
          "type": "string"
        },
        "customerName": {
          "type": "string"
        },
        "questionId": {
          "format": "int32",
          "type": "integer"
        },
        "evaluationName": {
          "type": "string"
        },
        "starRating": {
          "format": "int32",
          "type": "integer"
        },
        "answerText": {
          "type": "string"
        }
      }
    },
    "QuickMembership": {
      "required": [
        "status"
      ],
      "type": "object",
      "properties": {
        "groupId": {
          "format": "int32",
          "type": "integer"
        },
        "status": {
          "enum": [
            "Active",
            "Lapsed"
          ],
          "type": "string"
        }
      }
    },
    "GBToken": {
      "type": "object",
      "properties": {
        "guestBookTokenId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "token": {
          "type": "string"
        },
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "expiration": {
          "format": "date-time",
          "type": "string"
        },
        "url": {
          "type": "string"
        }
      }
    },
    "JsonPatchDocument[Jurisdiction]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[Jurisdiction]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[Jurisdiction]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "Order": {
      "type": "object",
      "properties": {
        "orderId": {
          "format": "int64",
          "type": "integer"
        },
        "externalOrderId": {
          "type": "string"
        },
        "customerId": {
          "format": "int32",
          "type": "integer"
        },
        "customerName": {
          "type": "string"
        },
        "customerEmail": {
          "type": "string"
        },
        "orderDate": {
          "format": "date-time",
          "type": "string"
        },
        "paymentStatus": {
          "type": "string"
        },
        "totalTax": {
          "format": "double",
          "type": "number"
        },
        "shipping": {
          "format": "double",
          "type": "number"
        },
        "shippingTax": {
          "format": "double",
          "type": "number"
        },
        "handling": {
          "format": "double",
          "type": "number"
        },
        "chargeFinal": {
          "format": "double",
          "type": "number"
        },
        "isTest": {
          "type": "boolean"
        },
        "marketingCode": {
          "type": "string"
        },
        "lastModifiedDate": {
          "format": "date-time",
          "type": "string"
        },
        "orderItems": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/OrderItem"
          }
        },
        "transactions": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Transaction"
          }
        }
      }
    },
    "OrderItem": {
      "required": [
        "paymentStatus",
        "productType"
      ],
      "type": "object",
      "properties": {
        "orderItemId": {
          "format": "int64",
          "type": "integer"
        },
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "eventTimeId": {
          "format": "int32",
          "type": "integer"
        },
        "paymentStatus": {
          "enum": [
            "Refunded",
            "Paid"
          ],
          "type": "string"
        },
        "itemQuantity": {
          "format": "int32",
          "type": "integer"
        },
        "finalPrice": {
          "format": "double",
          "type": "number"
        },
        "tax": {
          "format": "double",
          "type": "number"
        },
        "productType": {
          "enum": [
            "LiveEvent",
            "Webcast",
            "Replay",
            "OnDemand",
            "VideoDownload",
            "DVD",
            "CD",
            "Webinar",
            "Books",
            "TextBasedCE",
            "Other",
            "Classroom",
            "SCORM",
            "OtherDigital",
            "EBook",
            "VirtualSummit"
          ],
          "type": "string"
        },
        "productTypeLabel": {
          "type": "string"
        },
        "sku": {
          "type": "string"
        },
        "eventDate": {
          "format": "date-time",
          "type": "string"
        },
        "productName": {
          "type": "string"
        },
        "priceAdjustmentId": {
          "format": "int32",
          "type": "integer"
        },
        "priceAdjustmentName": {
          "type": "string"
        },
        "discountId": {
          "format": "int32",
          "type": "integer"
        },
        "discountName": {
          "type": "string"
        },
        "registrations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Registration"
          }
        }
      }
    },
    "Transaction": {
      "required": [
        "type",
        "status",
        "method"
      ],
      "type": "object",
      "properties": {
        "id": {
          "type": "string"
        },
        "type": {
          "enum": [
            "Payment",
            "Refund",
            "ChargeBack",
            "RewardsPoints",
            "FailPayment",
            "SettlementPending",
            "ModifyPaymentRefund"
          ],
          "type": "string"
        },
        "amount": {
          "format": "double",
          "type": "number"
        },
        "date": {
          "format": "date-time",
          "type": "string"
        },
        "captureDate": {
          "format": "date-time",
          "type": "string"
        },
        "status": {
          "enum": [
            "Pending",
            "Success",
            "Failed",
            "Cancelled",
            "Converted"
          ],
          "type": "string"
        },
        "method": {
          "enum": [
            "PayByCheck",
            "PayByPO",
            "PayByCash",
            "PayLater",
            "GiftCard",
            "API",
            "Import",
            "PaidOffline",
            "WriteOff",
            "VirtualTerminal",
            "Default",
            "MasterCard",
            "Visa",
            "AmericanExpress",
            "Discover",
            "Maestro",
            "JCB",
            "MatsterPass",
            "PayPalSmartCheckout",
            "ACH"
          ],
          "type": "string"
        }
      }
    },
    "Registration": {
      "required": [
        "status"
      ],
      "type": "object",
      "properties": {
        "registrationId": {
          "format": "int32",
          "type": "integer"
        },
        "customerId": {
          "format": "int32",
          "type": "integer"
        },
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "eventTimeId": {
          "format": "int32",
          "type": "integer"
        },
        "completionDate": {
          "format": "date-time",
          "type": "string"
        },
        "creditIssueDate": {
          "format": "date-time",
          "type": "string"
        },
        "creditsAdjustReason": {
          "type": "string"
        },
        "status": {
          "enum": [
            "Deactivated",
            "Active"
          ],
          "type": "string"
        },
        "totalCredits": {
          "type": "string"
        },
        "credits": {
          "type": "string"
        },
        "certificateLinks": {
          "type": "array",
          "items": {
            "type": "object"
          }
        },
        "timeRequired": {
          "format": "int32",
          "type": "integer"
        },
        "timeComplete": {
          "format": "int32",
          "type": "integer"
        },
        "archiveTimeRequired": {
          "format": "int32",
          "type": "integer"
        },
        "archiveTimeComplete": {
          "format": "int32",
          "type": "integer"
        },
        "externalId": {
          "type": "object"
        },
        "sku": {
          "type": "object"
        },
        "orderId": {
          "format": "int64",
          "type": "integer"
        },
        "customer": {
          "$ref": "#/definitions/Customer"
        },
        "product": {
          "$ref": "#/definitions/Product"
        }
      }
    },
    "Product": {
      "required": [
        "productId",
        "eventTimeId",
        "productType",
        "name",
        "unPublishType"
      ],
      "type": "object",
      "properties": {
        "productId": {
          "format": "int32",
          "type": "integer"
        },
        "eventTimeId": {
          "format": "int32",
          "type": "integer"
        },
        "productType": {
          "enum": [
            "LiveEvent",
            "Webcast",
            "Replay",
            "OnDemand",
            "VideoDownload",
            "DVD",
            "CD",
            "Webinar",
            "Books",
            "TextBasedCE",
            "Other",
            "Classroom",
            "SCORM",
            "OtherDigital",
            "EBook",
            "VirtualSummit"
          ],
          "type": "string"
        },
        "name": {
          "type": "string"
        },
        "sku": {
          "type": "string"
        },
        "brochure": {
          "type": "string"
        },
        "producer": {
          "type": "string"
        },
        "productTypeLabel": {
          "type": "string"
        },
        "shortDescription": {
          "type": "string"
        },
        "fullDescription": {
          "type": "string"
        },
        "courseLevelId": {
          "format": "int32",
          "type": "integer"
        },
        "courseLevel": {
          "type": "string"
        },
        "displayDuration": {
          "type": "string"
        },
        "originalDate": {
          "format": "date-time",
          "description": "(Non-live Only) Date of original recording.",
          "type": "string"
        },
        "duration": {
          "format": "int32",
          "description": "(Non-live Only) Duration in minutes.",
          "type": "integer"
        },
        "startDateTime": {
          "format": "date-time",
          "description": "(Live Only) Start time of the event.",
          "type": "string"
        },
        "endDateTime": {
          "format": "date-time",
          "description": "(Live Only) End time of the event.",
          "type": "string"
        },
        "publishDateTime": {
          "format": "date-time",
          "description": "(All types) Datetime when product will be added to the catalog.",
          "type": "string"
        },
        "unPublishDateTime": {
          "format": "date-time",
          "description": "(Non-live Only) Datetime when product will be removed from the catalog.",
          "type": "string"
        },
        "unPublishType": {
          "description": "(Live Only) How the UnPublishDuration is to be applied. (after event begins, after event ends, before event begins)",
          "enum": [
            "AfterEventBegins",
            "AfterEventEnds",
            "BeforeEventBegins"
          ],
          "type": "string"
        },
        "unPublishDuration": {
          "format": "int32",
          "description": "(Live Only) The duration in MINUTES when the product will be removed from the catalog. Requires UnPublishType to also be set.",
          "type": "integer"
        },
        "totalCredits": {
          "type": "string"
        },
        "price": {
          "format": "double",
          "type": "number"
        },
        "additionalPrice": {
          "format": "double",
          "type": "number"
        },
        "parentProductId": {
          "format": "int32",
          "type": "integer"
        },
        "parentName": {
          "type": "string"
        },
        "createdDateTime": {
          "format": "date-time",
          "type": "string"
        },
        "modifiedDateTime": {
          "format": "date-time",
          "type": "string"
        },
        "credits": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Credit"
          }
        }
      }
    },
    "QuickOrder": {
      "required": [
        "registrants"
      ],
      "type": "object",
      "properties": {
        "customerId": {
          "format": "int32",
          "type": "integer"
        },
        "externalId": {
          "type": "string"
        },
        "externalOrderId": {
          "type": "string"
        },
        "isPaid": {
          "type": "boolean"
        },
        "registrants": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/QuickRegistrant"
          }
        }
      }
    },
    "QuickRegistrant": {
      "type": "object",
      "properties": {
        "eventTimeId": {
          "format": "int32",
          "type": "integer"
        },
        "sku": {
          "type": "string"
        },
        "customerId": {
          "format": "int32",
          "type": "integer"
        },
        "externalId": {
          "type": "string"
        },
        "price": {
          "format": "double",
          "type": "number"
        }
      }
    },
    "JsonPatchDocument[Order]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[Order]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[Order]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "PriceAdjustment": {
      "required": [
        "name",
        "trigger",
        "beginPriceAdjustmentUnit",
        "endPriceAdjustmentUnit"
      ],
      "type": "object",
      "properties": {
        "priceAdjustmentId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "templateName": {
          "type": "string"
        },
        "percentOff": {
          "format": "double",
          "description": "Require only one of percentOff, amountOff, setPrice",
          "type": "number"
        },
        "amountOff": {
          "format": "double",
          "description": "Require only one of percentOff, amountOff, setPrice",
          "type": "number"
        },
        "setPrice": {
          "format": "double",
          "description": "Require only one of percentOff, amountOff, setPrice",
          "type": "number"
        },
        "resultingPrice": {
          "format": "double",
          "type": "number",
          "readOnly": true
        },
        "trigger": {
          "enum": [
            "NoTrigger",
            "Code",
            "TimeBased"
          ],
          "type": "string"
        },
        "discountCode": {
          "description": "Require if Code Trigger",
          "type": "string"
        },
        "beginPriceAdjustment": {
          "format": "int32",
          "description": "Require if TimeBased Trigger",
          "type": "integer"
        },
        "beginPriceAdjustmentUnit": {
          "description": "Require if TimeBased Trigger",
          "enum": [
            "Day",
            "Week",
            "Month"
          ],
          "type": "string"
        },
        "endPriceAdjustment": {
          "format": "int32",
          "description": "Require if TimeBased Trigger",
          "type": "integer"
        },
        "endPriceAdjustmentUnit": {
          "description": "Require if TimeBased Trigger",
          "enum": [
            "Day",
            "Week",
            "Month"
          ],
          "type": "string"
        },
        "activeDatetime": {
          "format": "date-time",
          "type": "string"
        },
        "expireDatetime": {
          "format": "date-time",
          "type": "string"
        },
        "maxUsage": {
          "format": "int32",
          "type": "integer"
        },
        "quantityLimit": {
          "format": "int32",
          "type": "integer"
        },
        "registrantTypeId": {
          "format": "int32",
          "type": "integer"
        },
        "stackable": {
          "type": "boolean"
        },
        "showName": {
          "type": "boolean"
        },
        "showAmountOff": {
          "type": "boolean"
        },
        "showInWidgetsAndDetails": {
          "type": "boolean"
        },
        "showSoldOut": {
          "type": "boolean"
        },
        "showExpireDate": {
          "type": "boolean"
        },
        "includeInRegistrantCount": {
          "type": "boolean"
        },
        "topOfList": {
          "type": "boolean"
        },
        "groups": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Group"
          }
        }
      }
    },
    "TemplatePriceAdjustment": {
      "type": "object",
      "properties": {
        "templateId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "percentOff": {
          "format": "double",
          "type": "number"
        },
        "amountOff": {
          "format": "double",
          "type": "number"
        },
        "setPrice": {
          "format": "double",
          "type": "number"
        },
        "activeDatetime": {
          "format": "date-time",
          "type": "string"
        },
        "expireDatetime": {
          "format": "date-time",
          "type": "string"
        },
        "maxUsage": {
          "format": "int32",
          "type": "integer"
        },
        "quantityLimit": {
          "format": "int32",
          "type": "integer"
        }
      }
    },
    "JsonPatchDocument[PriceAdjustment]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[PriceAdjustment]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[PriceAdjustment]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "QuickProduct": {
      "required": [
        "productType",
        "name"
      ],
      "type": "object",
      "properties": {
        "parentProductId": {
          "format": "int32",
          "type": "integer"
        },
        "parentName": {
          "type": "string"
        },
        "productType": {
          "enum": [
            "LiveEvent",
            "Webcast",
            "Replay",
            "OnDemand",
            "VideoDownload",
            "DVD",
            "CD",
            "Webinar",
            "Books",
            "TextBasedCE",
            "Other",
            "Classroom",
            "SCORM",
            "OtherDigital",
            "EBook",
            "VirtualSummit"
          ],
          "type": "string"
        },
        "name": {
          "type": "string"
        },
        "shortDescription": {
          "type": "string"
        },
        "fullDescription": {
          "type": "string"
        },
        "courseLevelId": {
          "format": "int32",
          "type": "integer"
        },
        "displayDuration": {
          "type": "string"
        },
        "originalDate": {
          "format": "date-time",
          "description": "(Non-live Only) Date of original recording.",
          "type": "string"
        },
        "duration": {
          "format": "int32",
          "description": "(Non-live Only) Duration in minutes.",
          "type": "integer"
        },
        "startDateTime": {
          "format": "date-time",
          "description": "(Live Only) Start time of the event.",
          "type": "string"
        },
        "endDateTime": {
          "format": "date-time",
          "description": "(Live Only) End time of the event.",
          "type": "string"
        },
        "totalCredits": {
          "type": "string"
        },
        "price": {
          "format": "double",
          "type": "number"
        },
        "sku": {
          "type": "string"
        }
      }
    },
    "JsonPatchDocument[Product]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[Product]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[Product]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "CourseLevel": {
      "type": "object",
      "properties": {
        "courseLevelId": {
          "format": "int32",
          "type": "integer"
        },
        "label": {
          "type": "string"
        },
        "description": {
          "type": "string"
        }
      }
    },
    "TemplateProduct": {
      "required": [
        "templateId",
        "name"
      ],
      "type": "object",
      "properties": {
        "templateId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "parentProductId": {
          "format": "int32",
          "description": "[Optional] Will add the new product to an existing family.",
          "type": "integer"
        }
      }
    },
    "Speaker": {
      "type": "object",
      "properties": {
        "speakerId": {
          "format": "int32",
          "type": "integer"
        },
        "externalId": {
          "type": "string"
        },
        "email": {
          "type": "string"
        },
        "prefix": {
          "type": "string"
        },
        "firstName": {
          "type": "string"
        },
        "middleName": {
          "type": "string"
        },
        "lastName": {
          "type": "string"
        },
        "suffix": {
          "type": "string"
        },
        "credential": {
          "type": "string"
        },
        "jobTitle": {
          "type": "string"
        },
        "companyName": {
          "type": "string"
        },
        "companyId": {
          "format": "int32",
          "type": "integer"
        },
        "company": {
          "$ref": "#/definitions/Company"
        },
        "biography": {
          "type": "string"
        },
        "image": {
          "$ref": "#/definitions/Image"
        },
        "address": {
          "$ref": "#/definitions/Address"
        },
        "customFields": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/CustomField"
          }
        }
      }
    },
    "JsonPatchDocument[Speaker]": {
      "type": "object",
      "properties": {
        "operations": {
          "type": "array",
          "items": {
            "$ref": "#/definitions/Operation[Speaker]"
          },
          "readOnly": true
        }
      }
    },
    "Operation[Speaker]": {
      "type": "object",
      "properties": {
        "value": {
          "type": "object"
        },
        "path": {
          "type": "string"
        },
        "op": {
          "type": "string"
        },
        "from": {
          "type": "string"
        }
      }
    },
    "Venue": {
      "required": [
        "status",
        "type"
      ],
      "type": "object",
      "properties": {
        "venueId": {
          "format": "int32",
          "type": "integer"
        },
        "name": {
          "type": "string"
        },
        "status": {
          "enum": [
            "Pending",
            "Confirmed"
          ],
          "type": "string"
        },
        "type": {
          "enum": [
            "Public",
            "Private"
          ],
          "type": "string"
        },
        "phone": {
          "type": "string"
        },
        "webUrl": {
          "type": "string"
        },
        "address": {
          "$ref": "#/definitions/Address"
        },
        "timeZoneId": {
          "type": "string"
        }
      }
    }
  },
  "securityDefinitions": {
    "oauth2": {
      "type": "oauth2",
      "description": "OAuth2 Client Credentials Grant",
      "flow": "application",
      "tokenUrl": "/token/service/{tenantId}",
      "scopes": {
        "service": "Access to all service resources"
      }
    }
  }
}
