# Intro Showcase View
[![Android Arsenal]( https://img.shields.io/badge/Android%20Arsenal-Intro--showcase--view-green.svg?style=flat )]( https://android-arsenal.com/details/1/8387 )
<img alt="Badge" height="20px" src="https://androidweekly.net/issues/issue-506/badge">


<img src="assets/4-%20intro%20showcase.jpg" />


An android library to highlight different features of the app built using Jetpack Compose.

The library is inspired by the [TapTargetView](https://github.com/KeepSafe/TapTargetView) that is useful for legacy views.


<img src="assets/main_intro.gif" height="540" />

## Configuration

Available on [Maven Central](https://search.maven.org/artifact/com.canopas.intro-showcase-view/introshowcaseview).

Add the dependency
```gradle
implementation 'com.canopas.intro-showcase-view:introshowcaseview:1.0.5'
```

## How to use ?
```kotlin
@Composable
fun ShowcaseSample() {
    val introShowCaseState = rememberIntroShowCaseState()

    var showAppIntro by remember {
        mutableStateOf(true)
    }

    Box {
        FloatingActionButton(
            onClick = {},
            modifier = Modifier.introShowCaseTarget(
                state = introShowCaseState,
                index = 0,
                style = ShowcaseStyle.Default.copy(
                    backgroundColor = Color(0xFF1C0A00), // specify color of background
                    backgroundAlpha = 0.98f, // specify transparency of background
                    targetCircleColor = Color.White // specify color of target circle
                ),
                // specify the content to show to introduce app feature
                content = {
                    Column {
                        Text(
                            text = "Check emails",
                            color = Color.White,
                            fontSize = 24.sp,
                            fontWeight = FontWeight.Bold
                        )
                        Text(
                            text = "Click here to check/send emails",
                            color = Color.White,
                            fontSize = 16.sp
                        )
                        Spacer(modifier = Modifier.height(10.dp))
                        Icon(
                            painterResource(id = R.drawable.right_arrow),
                            contentDescription = null,
                            modifier = Modifier
                                .size(80.dp)
                                .align(Alignment.End),
                            tint = Color.White
                        )
                    }
                }
            ),
            backgroundColor = ThemeColor,
            contentColor = Color.White,
            elevation = FloatingActionButtonDefaults.elevation(6.dp)
        ) {
            Icon(
                Icons.Filled.Email,
                contentDescription = "Email"
            )
        }

        if (showAppIntro) {
            IntroShowCase(introShowCaseState) {
                //App Intro finished!!
                showAppIntro = false
            }
        }
    }
}
```
<img src="assets/intro2.gif" height="480" />
<img src="assets/intro3.gif" height="480" />

# Demo
[Sample](https://github.com/canopas/Intro-showcase-view/tree/master/app) app demonstrates how simple the usage of the library actually is.

# Interested in library implementation?
Checkout the [Article](https://blog.canopas.com/intro-showcase-view-in-jetpack-compose-ac044cd3bf28)

# Bugs and Feedback
For bugs, questions and discussions please use the [Github Issues](https://github.com/canopas/JetTapTarget/issues).

# Credits

Intro showcaseview is owned and maintained by the [Canopas team](https://canopas.com/). You can follow them on Twitter at [@canopassoftware](https://twitter.com/canopassoftware) for project updates and releases.
