# NX Daemon is not running. The watch command is not supported without

```shell
# 1. Nx Daemon in DIESEM Terminal hart aktivieren
$env:NX_DAEMON = "true"

# 2. Falls dein Terminal aus irgendeinem Grund wie CI aussieht: aktuelle Shell bereinigen
"CI","GITHUB_ACTIONS","GITLAB_CI","TF_BUILD","BUILD_BUILDID","TEAMCITY_VERSION","JENKINS_URL" | ForEach-Object {
    Remove-Item "Env:\$_" -ErrorAction SilentlyContinue
}

# 3. Nx Daemon-State sauber wegwerfen
pnpm exec nx reset --only-daemon

# 4. Daemon explizit starten
pnpm exec nx daemon --start --verbose

# 5. Status anzeigen
pnpm exec nx daemon
```
