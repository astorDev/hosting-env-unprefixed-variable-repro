# hosting-env-unprefixed-variable-repro

Minimal reproduction project for "Unprefixed Hosting Environment Variable is ignored"

# Recreating this example

1. Create a new web project

```sh
dotnet new web
```

2. Run it setting "ENVIRONMENT" environment variable

```sh
export ENVIRONMENT=Repro && dotnet run
```

3. Search the logs for `Hosting environment:`

|Expected|Actual|
|---|---|
|Hosting environment: Repro|Hosting environment: Development|

## Note

I was leaning to assume that the variable is ignored since it's overriden by launchSettings. But first, deleting launchSettings doesn't make a difference in the problem (only changed Development to Production). And for other variables unprefixed variables take precedence over variables prefixed with `ASPNETCORE_`
