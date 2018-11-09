# @bbc/cypress
**See https://github.com/cypress-io/cypress/issues/2694 for the reason behind this fork. Use at your own risk!**

## Cypress
This is a form of Cypress so that it can provide the ability to pass PKI cert options to `cy.visit()`. This allows us to test against cert protected domains. See https://github.com/cypress-io/cypress/issues/2694 for more information.

This is very much a WIP and designd as a *temporary* solution to unblock us from using Cypress while the conversation on their repository is ongoing. There is no desire to continue to maintain a fork, and work is underway to try and help Cypress define requirements and/or implement this into the core product.

## Versioning
We're using pre-release versioning of the semantic version spec. We consider these changes a feature level change to the Cypress product, and therefore our version number is based on being a prerelease of the next feature version of Cypress. 

e.g.

`3.2.0-1.0.0` indicates that this is a proposed feature level release of Cypress, and that we have forked from 3.1.x - and 1.0.0 relates to the specific implementation of the certificate feature carried out from within the fork.

If Cypress release a 3.2.0 before our changes are implemented, and we merge that into the fork, then our version number would become `3.3.0-1.0.0` as this would represent a pre-release of the next feature point release of Cypress.


## Usage
```
# Export CYPRESS prefixed environment variables containing the contents of the crt/key files

export CYPRESS_CERT=$(cat /path/to/your/certificate.crt)
export CYPRESS_KEY=$(cat /path/to/your/certificate.key)

# Start Cypress however you normally would
cypress:open
```

```javascript
# index_spec.js

describe(('when accessing a PKI cert protected domain') => {
  it(('should not reject with an error') => {
      const options = {
          cert: Cypress.env('CERT'),
          key: Cypress.env('KEY')
      }
      
      cy.visit('https://cert-protected-domain', options)
  })
});
```

## Install
```sh
npm install --save-dev @bbc/cypress
```

## Documentation

Please [visit the original documentation](https://on.cypress.io/cli) for a full list of commands and examples. Other than the support for certificates there are no differences between this fork and the corresponding version of Cypress.
