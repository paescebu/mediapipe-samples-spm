# Deprecated

This fork is no longer maintained.

It existed to build the MediaPipe iOS samples with Swift Package Manager, and Google now publishes that support. The Xcode projects here still depend on [SwiftTasksVision](https://github.com/paescebu/SwiftTasksVision), [SwiftTasksText](https://github.com/paescebu/SwiftTasksText), and [SwiftTasksGenAI](https://github.com/paescebu/SwiftTasksGenAI). Use Google's package and the upstream samples for new work.

- Samples: [google-ai-edge/mediapipe-samples](https://github.com/google-ai-edge/mediapipe-samples)
- Swift package: [google-ai-edge/mediapipe](https://github.com/google-ai-edge/mediapipe) (`Package.swift` on `master`)
- Setup guide: [Setup guide for iOS](https://developers.google.com/edge/mediapipe/solutions/setup_ios)

Select the product that matches the task:

- Vision: `MediaPipeTasksVision`
- Text: `MediaPipeTasksText`
- Audio: `MediaPipeTasksAudio`

`MediaPipeTasksCommon` is included automatically with each of those products. The same manifest also publishes `MediaPipeTasksRetrieval` and `MediaPipeTasksDecision`. It requires iOS 15. The on-device LLM sample in this fork was wired to SwiftTasksGenAI; current LLM samples are in the upstream repository.

### Xcode

With the project open, choose **File > Add Package Dependencies...** and enter:

```
https://github.com/google-ai-edge/mediapipe
```

Select the `mediapipe` package, choose a dependency rule (Up to Next Major Version, or the `master` branch), then add `MediaPipeTasksVision`, `MediaPipeTasksText`, or `MediaPipeTasksAudio` to the app target.

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

Use `MediaPipeTasksText` or `MediaPipeTasksAudio` in place of `MediaPipeTasksVision` when that is the library you need. The [iOS setup guide](https://developers.google.com/edge/mediapipe/solutions/setup_ios) is the source for the current steps.

---

The original README follows.

This repo hosts the official MediaPipe samples with a goal of showing the fundamental steps involved to create apps with our machine learning platform. 

External PRs for fixes are welcome, however new sample/demo PRs will likely be rejected to maintain the simplicity of this repo for ongoing maintenance. It is strongly recommended that contributors who are interested in submitting more complex samples or demos host their samples in their own public repos and create written tutorials to share with the community. Contributors can also submit these projects and tutorials to the [Google DevLibrary](https://devlibrary.withgoogle.com/)


MediaPipe Solutions streamlines on-device ML development and deployment with flexible low-code / no-code tools that provide the modular building blocks for creating custom high-performance solutions for cross-platform deployment. It consists of the following components:
* MediaPipe Tasks (low-code): create and deploy custom e2e ML solution pipelines
* MediaPipe Model Maker (low-code): create custom ML models from advanced solutions
* MediaPipe Studio (no-code): create, evaluate, debug, benchmark, prototype, deploy advanced production-level solutions