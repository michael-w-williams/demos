# `fn deploy`

```yaml
$ fn deploy

DEVELOPMENT COMMANDS
  fn deploy -   Deploys a function to the functions server. (bumps, build, pushes and updates route)
                
USAGE
  fn deploy [global options]  [command options]
    
DESCRIPTION
  This is the description
    
COMMAND OPTIONS
  --app value                     App name to deploy to
  --verbose, -v                   Verbose mode
  --no-cache                      Don't use Docker cache for the build
  --local, --skip-push            Do not push Docker built images onto Docker Hub - useful for local development.
  --registry --registry username  Set the Docker owner for images and optionally the registry. This will be prefixed to your function name for pushing to Docker registries.
  --all app.yaml                  If in root directory containing app.yaml, this will deploy all functions
  --no-bump                       Do not bump the version, assuming external version management
  --build-arg value               Set build time variables
  --working-dir value, -w value   Specify the working directory to deploy a function, must be the full path.
  
```

[Some link](#)
