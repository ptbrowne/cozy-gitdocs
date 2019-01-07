You've successfully created your connector and saved your personal data a service you're using. Now, you want to help others free their data, it's great ! To allow other users to use your connector, it must be packaged and sent to the store.

<!-- MarkdownTOC autolink=true -->

- [Integration in the store for all the users](#integration-in-the-store-for-all-the-users)
    - [Icon](#icon)
    - [Package.json](#packagejson)
    - [Manifest.konnector](#manifestkonnector)

<!-- /MarkdownTOC -->


## Integration in the store for all the users

To run a connector, we do not want the cozy to install all dependencies of the connector each time
it installs it.

To avoid this, the connectors need to be compiled into one file in a dedicated branch of the
repository and the repository needs to be a public git repository. The `package.json` file
from [cozy-konnector-template] gives you the commands to do this : `yarn build` and `yarn deploy`
but the last one needs to be configured in `package.json`

Once your public git repository is configured, you only have to declare it.

Cozy will soon have a store for connectors and you will be able to publish connectors yourself. But
at the moment, you need to declare your new connector on the [cozy forum](https://forum.cozy.io).
The Cozy team will review your code and add your connector to the [Cozy Collect] application.

To make the connector available more quickly for all cozys, you can follow this few steps of
packaging:

### Icon

You need to push an icon in `assets/`. Please respect this rules :

 - Square icon, possibly a png or svg
 - Try the Apple app store icon if needed

### Package.json

 - Edit the name to be cozy-konnector-<slug\>
 - Edit the repository URL
 - Edit the command `deploy` with the correct repository URL

### Manifest.konnector

 - Edit the name with a nice name (Capitals and spaces allowed here)
 - Edit icon as needed
 - Edit slug
 - Edit source with the correct repository URL
 - Add a correct vendor link
 - Choose one or more categories in this list : `banking, shopping, insurance, isp, telecom, energy, public_service, other`
 - If needed, change the input type the target website use to login the user: `text`, `email` or `phone` for instance, this will enforce pre-checking
 - Edit for both locales `en` and `fr` the short description and long description
