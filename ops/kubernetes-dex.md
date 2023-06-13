# Kubernetes and DEX

Setting up kubernetes with dex authentication and authorization
- https://medium.com/trendyol-tech/kubernetes-authentication-and-authorization-through-dex-ldap-and-rbac-rules-c2e03111b408
- https://kubernetes.io/docs/reference/access-authn-authz/rbac/#clusterrolebinding-example
- https://www.youtube.com/watch?v=ax0gJPKgsdU (not watched)

keycloak vs dex:
- https://medium.com/@sct10876/keycloak-vs-dex-71f7fab29919

dex via gitlab as alternative?

keycloak + kubernetes:
- https://www.keycloak.org/getting-started/getting-started-kube

Kubernetes authentication via GitHub OAuth and Dex:
- https://medium.com/preply-engineering/k8s-auth-a81f59d4dff6

GitLab as OpenID Connect identity provider:
- https://docs.gitlab.com/ee/integration/openid_connect_provider.html
- maybe these user infos provided by gitlab are useful for k8s
  - groups_direct
  - https://gitlab.org/claims/groups/owner
  - https://gitlab.org/claims/groups/maintainer
  - https://gitlab.org/claims/groups/developer
