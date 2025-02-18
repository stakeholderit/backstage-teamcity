# Backstage teamcity plugin

Welcome to the teamcity plugin for Backstage!

## Getting started
Install via yarn
```
yarn --cwd packages/app add @stakeholderit/backstage-plugin-teamcity
```

In: packages\app\src\components\catalog\EntityPage.tsx file add:
```
import { isTeamcityAvailable, EntityTeamcityContent } from 'backstage-plugin-teamcity';
```

Then under cicdContent block in the EntityPage.tsx file paste:
```
    <EntitySwitch.Case if={isTeamcityAvailable}>
        <Grid item sm={12}>
            <EntityTeamcityContent/>
        </Grid>
    </EntitySwitch.Case>
```

As a final step add the proxy to the app-config.local.yaml or prod depending on the env.

```
proxy:
  '/teamcity-proxy/':
    target: 'http://localhost:8111'
    headers:
      Authorization: 'Basic BASIC_AUTH'
      Accept: 'application/json'
```

# Project catalog flag requirement
```
  annotations:
    teamcity/project-id: TEAMCITY_NAME
```

# Screenshots
![error](https://github.com/stakeholderit/backstage-teamcity/blob/main/assets/sample.jpg)
![error](https://github.com/stakeholderit/backstage-teamcity/blob/main/assets/history.jpg)
![error](https://github.com/stakeholderit/backstage-teamcity/blob/main/assets/log.jpg)

# Developing

## Installing packages
Run `yarn install`

## Running tests

To run tests execute `yarn test a`
