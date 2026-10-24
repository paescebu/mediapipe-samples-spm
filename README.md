> [!WARNING]
> **This fork is deprecated and no longer maintained.** Google now provides official Swift Package Manager support for MediaPipe Tasks. Please use [google-ai-edge/mediapipe](https://github.com/google-ai-edge/mediapipe) and the upstream samples at [google-ai-edge/mediapipe-samples](https://github.com/google-ai-edge/mediapipe-samples).

## Why is this deprecated?

This fork added Swift Package Manager support to the MediaPipe iOS samples by depending on SwiftTasksVision, SwiftTasksText, and SwiftTasksGenAI. Google now publishes MediaPipe Tasks for iOS from [google-ai-edge/mediapipe](https://github.com/google-ai-edge/mediapipe), and the [upstream samples](https://github.com/google-ai-edge/mediapipe-samples) already use that package. This fork will not receive further updates.

## Migrating to the official package

### Xcode

1. With your project open in Xcode, select **File > Add Package Dependencies...**.
2. Enter the repository URL: `https://github.com/google-ai-edge/mediapipe`
3. Select the `mediapipe` package and choose a dependency rule (for example, Up to Next Major Version, or the `master` branch).
4. Click **Add Package**.
5. Select the library your app needs and add it to the app target:
   - Vision tasks: `MediaPipeTasksVision`
   - Text tasks: `MediaPipeTasksText`
   - Audio tasks: `MediaPipeTasksAudio`

`MediaPipeTasksCommon` is included automatically.

### Package.swift

```swift
dependencies: [
    .package(
        url: "https://github.com/google-ai-edge/mediapipe",
        branch: "master"
    ),
],
targets: [
    .target(
        name: "MyAppTarget",
        dependencies: [
            .product(name: "MediaPipeTasksVision", package: "mediapipe"),
        ]
    ),
]
```

| This fork's packages | Official replacement |
| --- | --- |
| [SwiftTasksVision](https://github.com/paescebu/SwiftTasksVision) | `MediaPipeTasksVision` |
| [SwiftTasksText](https://github.com/paescebu/SwiftTasksText) | `MediaPipeTasksText` |
| [SwiftTasksGenAI](https://github.com/paescebu/SwiftTasksGenAI) | [`LiteRTLM`](https://github.com/google-ai-edge/LiteRT-LM). Not a product of the MediaPipe Swift package. The [LLM Inference guide for iOS](https://developers.google.com/edge/mediapipe/solutions/genai/llm_inference/ios) marks that API maintenance-only and recommends the [LiteRT-LM Swift API](https://developers.google.com/edge/litert-lm/swift). CocoaPods pods `MediaPipeTasksGenAI` and `MediaPipeTasksGenAIC` remain for the maintenance API. |

**Docs:** [Setup guide for iOS](https://developers.google.com/edge/mediapipe/solutions/setup_ios)

## Thank you

Thank you for using this fork while official Swift Package Manager support was still missing. Please file new issues and sample changes on the upstream repositories.

---

This repo hosts the official MediaPipe samples with a goal of showing the fundamental steps involved to create apps with our machine learning platform. 

External PRs for fixes are welcome, however new sample/demo PRs will likely be rejected to maintain the simplicity of this repo for ongoing maintenance. It is strongly recommended that contributors who are interested in submitting more complex samples or demos host their samples in their own public repos and create written tutorials to share with the community. Contributors can also submit these projects and tutorials to the [Google DevLibrary](https://devlibrary.withgoogle.com/)


MediaPipe Solutions streamlines on-device ML development and deployment with flexible low-code / no-code tools that provide the modular building blocks for creating custom high-performance solutions for cross-platform deployment. It consists of the following components:
* MediaPipe Tasks (low-code): create and deploy custom e2e ML solution pipelines
* MediaPipe Model Maker (low-code): create custom ML models from advanced solutions
* MediaPipe Studio (no-code): create, evaluate, debug, benchmark, prototype, deploy advanced production-level solutions