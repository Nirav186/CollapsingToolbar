# Collapsing Toolbar Jetpack Compose

A simple and customizable collapsing toolbar library for Jetpack Compose. This library allows you to implement a smooth and efficient collapsing toolbar in your Compose-based Android applications.

## Features

- **Smooth animation** for collapsing toolbar
- **Flexible customization** for expanded and collapsed views
- **Support for two rows** in the app bar (expandable and collapsed states)
- Easy integration with Jetpack Compose’s `TopAppBar` and scroll behavior

## Installation

You can integrate the `Collapsing Toolbar Jetpack Compose` library into your project using either **Gradle** or **Maven**.

### Gradle

1. Add the following repositories to your `build.gradle` file:

```gradle
repositories {
    mavenCentral()
    maven { url 'https://www.jitpack.io' }
}
```

2. Add the dependency in the dependencies block:

```gradle
dependencies {
    implementation 'com.github.Nirav186:CollapsingToolbar:Tag'
}
```

### Maven
1. Add the repositories in your pom.xml file:
```
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://www.jitpack.io</url>
    </repository>
    <repository>
        <id>mavenCentral</id>
        <url>https://repo.maven.apache.org/maven2</url>
    </repository>
</repositories>
```

2. Add the following dependency in your pom.xml:
```
<dependency>
    <groupId>com.github.Nirav186</groupId>
    <artifactId>CollapsingToolbar</artifactId>
    <version>Tag</version>
</dependency>
```

### Usage

Here’s a simple example of how to use the Collapsing Toolbar in Jetpack Compose:
```
val scrollBehavior = TopAppBarDefaults.enterAlwaysScrollBehavior(rememberTopAppBarState())

val isCollapsed: Boolean by remember {
    derivedStateOf {
        scrollBehavior.state.collapsedFraction > 0.5f
    }
}

TwoRowsTopAppBar(
    modifier = Modifier
        .padding(0.dp)
        .fillMaxWidth()
        .layout { measurable, constraints ->
            val paddingCompensation = 16.dp.toPx().roundToInt()
            val adjustedConstraints = constraints.copy(
                maxWidth = constraints.maxWidth + paddingCompensation
            )
            val placeable = measurable.measure(adjustedConstraints)
            layout(placeable.width, placeable.height) {
                placeable.place(-paddingCompensation / 2, 0)
            }
        },
    title = {
        // Expanded content here
    },
    titleTextStyle = MaterialTheme.typography.titleLarge,
    titleBottomPadding = 0.dp,
    smallTitle = {
        // Collapsed content here
    },
    smallTitleTextStyle = MaterialTheme.typography.titleSmall,
    navigationIcon = {
        // You can add a navigation icon here
    },
    actions = {
        // You can add actions here
    },
    windowInsets = TopAppBarDefaults.windowInsets,
    maxHeight = /* pass max height here */,
    pinnedHeight = if (isCollapsed.not()) 0.sdp else 92.sdp, // Only if needed
    scrollBehavior = scrollBehavior
)
```

### Customization
* Max Height: Define the maximum height of the toolbar.
* Pinned Height: Set the height when collapsed (useful for creating a smaller, pinned toolbar).
* Title Content: Customize the content for both expanded (title) and collapsed (smallTitle) states.

### Dependencies
* Jetpack Compose

### License
This project is licensed under the MIT License.

### Contact

For any inquiries or contributions, feel free to reach out:
Email: nrvrangapariya186@gmail.com
