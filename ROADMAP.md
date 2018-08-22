Roadmap
=======

V1 - BETA RC1 - Angular 6 migration
-----------------------------------

_Release: End of September 2018_

**Materia Designer**
- Migrate Materia Designer with angular6 (better perf / more polished UI)
- Monaco editor to edit files
- Colored terminal
- Enhanced File tree
- Virtual entities support (CF Materia Server)
- Actions support on queries (CF Materia Server)
- Instant live access to production server using Materia Server Admin REST API
- Boilerplate Angular / React / Vue client in 1 click
- New settings UI
- New Addon system migrated to angular6

**Materia Server**
- Admin REST API - it's the new way Materia Designer communicate with Materia Server, it allows instant Live production server access protected by password
- Virtual Entities - support for entities that are not stored in database (e.g. REST API)
- Actions - You can trigger an action after or before calling a query or an endpoint (e.g. send an email or save statistics)

**Materia Addons**
- Mailjet addon
- Sendgrid Addon
- Usermanagement Addon
- Facebook addon
- Firebase Authentication Addon
- Angular Universal Addon (SSR)
- Boilerplate addon to help developers to build new addons

**Videos**
- 2min video
- 10min video

**Materia Website**
- Migrated to Angular6
- Update documentation

V1 BETA RC-2
------------

**Materia Designer**
- Materia Accounts
- Materia Deployment on your own server
- Actions support on endpoints
- Endpoint realtime support (websocket)

**Materia Addons**
- Stripe addon

**Materia Website**
- Update documentation

V1
--

**Materia Designer**
- Subscriptions + free plan (cf pricing)
(Materia Server will always be free and open source)
- Materia Deployment to Materia Hosting in one click

**new => Materia Hosting**
- Custom domains support - DNS configurations


Road to V2
----------

**Materia Designer**
- Team Management
- Realtime collaboration
- Test suite to test your endpoints and queries in Materia Designer
- Mobile boilerplate React Native / Native Script / Ionic

**Materia Server**
- Server in typescript with build/watch support (allowJs: true)
- Merge model and custom queries in a typescript file
- Entity - Support JSON type

**Materia Cloud**
- Build your application in your web browser with the same interface than Materia Designer but in the browser
- Sync your local application with Materia Cloud

**Materia Addons**
- Upload Addon - Upload any files/images/video on the storage of your choice
- Admin addon (to generate an admin portal in your client)
- Twitter addon
- Google addon
- AWS addon
- Salesforce addon
- Swagger addon - Export your API in swagger

Road to V3
----------

**Materia Services** - Allow you to connect to other service like redis / mongodb or rabbitmq

**Materia Designer**
- New view to install / uninstall services
- Multiple type of entities (redis => key value store / mongodb => collection etc...) and different type of data visualization supported depending of the service the entity depends on.

**Materia Server**
- API - GraphQL support

Road to V4
----------

- UI & Component builder that generate Angular application that work with your API
