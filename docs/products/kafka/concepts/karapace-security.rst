Karapace security
=================

By default Karapace Schema Registry and Karapace REST Proxy security is limited to authentication. All authenticated users have full access to both. All users configured in the service have access. You can find the URL for both of these services in the Console. The URL embeds a username and password.

Karapace Schema Registry
------------------------

For more granular access control user authorization can be enabled in Karapace Schema Registry by enabling the flag `karapace_schema_registry_acl`. Authorization is only supported for Karapace Schema Registry, not for Confluent Schema Registry.

Karapace Schema Registry access control lists (ACL) is stored in Aiven platform and Aiven platform forwards the configured ACL to Karapace Schema Registry. Aiven Client can be used to manage entries int the ACL. Currently there's no UI support to manage the ACL.

When Karapace Schema Registry receives an HTTP request from an HTTP client, the incoming HTTP request contains username and credentials. Karapace Schema Registry authenticates the user. Karapace Schema Registry verifies that the user has access to the requested resource based on the ACL. Some endpoints do also filtering of the returned content based on the ACL.

Karapace REST Proxy
-------------------

For more granular access control user authorization can be enabled in Karapace REST Proxy by enabling the flag `karapace_rest_proxy_acl`.

When Karapace REST Proxy receives an HTTP request from an HTTP client, the incoming HTTP request contains username and credentials. Karapace REST Proxy uses these credentials when it connects to Aiven for Apache Kafka® and authenticates the connection. Kafka® uses access control lists (ACL) and will either allow or deny the request and return the response to Karapace REST Proxy. Karapace REST Proxy in turn forwards the response to the HTTP client.

