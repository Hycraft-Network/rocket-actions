# rocket-actions

Reusable GitHub Actions composite actions for Rocket API uploads.

## Actions

### upload-to-rocket

Downloads a GitHub artifact and uploads the JAR to the Rocket API via simple PUT.
Designed to run on **self-hosted runners** for maximum upload speed to your S3 storage.

#### Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `artifact-name` | Yes | — | Name of the GitHub artifact containing the JAR |
| `jar-filename` | Yes | — | Filename of the JAR inside the artifact |
| `namespace` | No | `plugins` | Rocket Vortex namespace |
| `rocket-api-key` | Yes | — | Rocket API key for authentication |

#### Usage

```yaml
jobs:
  upload-to-rocket:
    runs-on: [self-hosted]
    needs: publish
    steps:
      - uses: Hycraft-Network/rocket-actions/upload-to-rocket@v1
        with:
          artifact-name: my-plugin-jar
          jar-filename: MyPlugin.jar
          rocket-api-key: ${{ secrets.ROCKET_API_KEY }}
```
