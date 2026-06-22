# vbwd-android-subscription

A feature **plugin** for the [vbwd-android](https://github.com/vbwd-platform/vbwd-android-core)
plugin-host platform — the Kotlin · Jetpack Compose · Hilt port of the vbwd-ios
SDK. Plugin id: `subscription` · version `1.0.0`.

Subscription management — tarif plans, subscription overview, add-ons, a dashboard widget, and a checkout source.

## What it registers

Through the `PlatformSdk` facade (the single extension seam) this plugin contributes:
routes, dashboard widget, a SubscriptionCheckoutSource, translations, menu items.

It touches **no core internals** — it depends on the public `:core` module only
(Open/Closed). Depends on **`:core`** only.

## Consume it

As a standalone module the plugin is published to GitHub Packages and consumed by
Maven coordinate:

```kotlin
// settings.gradle.kts — add the GitHub Packages repo (PAT with read:packages)
dependencyResolutionManagement {
    repositories {
        maven {
            url = uri("https://maven.pkg.github.com/vbwd-platform/vbwd-android-subscription")
            credentials {
                username = System.getenv("GITHUB_ACTOR")
                password = System.getenv("GITHUB_TOKEN")
            }
        }
    }
}

// build.gradle.kts — register it in the host's available-plugins list
dependencies {
    implementation("com.vbwd:vbwd-android-subscription:1.0.0")
}
```

Then add it to the host's `provideAvailablePlugins` list and to
`app/src/main/assets/plugins.json` (the enable/disable manifest).

## Build & test

```bash
./gradlew check        # ktlint + detekt + unit tests
```

## Docs

- [`docs/architecture.md`](docs/architecture.md) — how this plugin is wired.
- Original sprint report: `docs/dev_log/20260619/reports/07-A05-subscription-plugin.md` in the umbrella repo.

## License

BSL 1.1 (Business Source License). Part of the **vbwd-platform** SDK.
