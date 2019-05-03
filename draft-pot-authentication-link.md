---
date: 2019-05-02
title: "Link relationship types for authentication"
docname: draft-pot-authentication-link-00
category: std
author:
 -
    ins: E. Pot
    name: Evert Pot
    email: me@evertpot.com
    uri: https://evertpot.com/
normative:
  RFC8288:

--- abstract

This specification defines a set of relationships that may be used
to indicate where a user may authenticate, log out, register a new
account or find out who is currently authenticated.

--- middle

# Introduction

{{RFC8288}} defines a framework and registry for Link Relationships types.
This specification defines a set of new relationship types to aid clients
in discovering endpoints for authentication and registration:
`authenticate`, `authenticated-as`, `logout` and `register-user`.

# authenticate

The `authenticate` can be used to link to a resource that hosts
a page where a user can authenticate itself for the current resource.

For example, this link might refer to a HTML login page.

Example:

~~~ html
<a href="/login" rel="authenticate">Login</a>
~~~

This specification doesn't define the authentication protocol. For example,
the link could refer to an OAuth2 authorization endpoint.

# authenticated-as

The `authenticated-as` link refers to a resource that describes the effective
authenticated user for a HTTP response.

Following this link might allow a client to answer the question 'who am I?'.
This might link to a user profile page, or it might link to an API that
returns a JSON response with user information.

Example:

~~~ http
Link: <https://api.example.org/users/123-abc>; rel="authenticated-as"
~~~

# logout

The `logout` refers to a resource where an authenticated user
might end their session.

In a browser this might clear cookies, or in the case of OAuth2 it could
revoke any active authentication tokens.

# register-user

The `register-user` Link Relation refers to a resource where a user might
sign up for a service for the context URI.

The linked resource might contain a HTML registration form, or otherwise
instructions that allow a client to find out how to sign up for the service.

# IANA considerations

This document defines `authenticate`, `authenticated-as`, `logout` and
`register-user` link relation types and adds them to the "Link Relations"
registry:

## authenticate link relation

- Relation name: authenticate
- Description: Refers to a resource where a client may authenticate for the
  the context URI.
- Reference: TBD

## authenticated-as link relation

- Relation name: authenticated-as
- Description: Refers to a resource that describes the authenticated entity
  for the HTTP response.
- Reference: TBD

## logout link relation

- Relation name: logout 
- Description: Refers to an endpoint where a client may invalidate the current
  authentication session.
- Reference: TBD

## register-user link relation

- Relation name: register-user
- Description: Refers to a resource where a client may create a new user
  account for the context URI.
- Reference: TBD

--- back

# Changelog

## Changes since -00

*
