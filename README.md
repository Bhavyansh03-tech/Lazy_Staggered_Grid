# Lazy Staggered Grid in Jetpack Compose

This project demonstrates a lazy vertical staggered grid layout in Jetpack Compose, featuring randomly colored boxes of varying heights.

## Features

- Lazy vertical staggered grid layout.
- Randomly colored boxes with dynamic heights.
- Smooth scrolling and spacing between items.

## Screenshot
<img src="https://github.com/user-attachments/assets/e24c53e2-905b-489f-a844-a5e7dc5aed24" alt="First Screenshot" style="width: 200px; height: auto">

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/Bhavyansh03-tech/Lazy_Staggered_Grid.git
    ```

2. Open the project in Android Studio.

3. Sync the project with Gradle files.

## Usage

To use this layout in your project, include the `LazyVerticalStaggeredGrid` and `RandomColorBox` composables. Here is a brief example:

```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val items = (1..100).map {
            ListItem(
                height = Random.nextInt(100, 300).dp,
                color = Color(
                    Random.nextLong(0xFFFFFFFF)
                ).copy(alpha = 0.7f)
            )
        }

        enableEdgeToEdge()
        setContent {
            LazyStaggeredGridTheme {
                LazyVerticalStaggeredGrid(
                    columns = StaggeredGridCells.Fixed(2),
                    modifier = Modifier.fillMaxSize(),
                    contentPadding = PaddingValues(16.dp),
                    horizontalArrangement = Arrangement.spacedBy(16.dp),
                    verticalItemSpacing = 16.dp
                ) {
                    items(items.size) {
                        RandomColorBox(items[it])
                    }
                }
            }
        }
    }
}

data class ListItem(
    val height: Dp,
    val color: Color
)

@Composable
fun RandomColorBox(item: ListItem) {
    Box(
        modifier = Modifier
            .fillMaxWidth()
            .height(item.height)
            .clip(RoundedCornerShape(10.dp))
            .background(item.color)
    )
}
```

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for any improvements or bug fixes.

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -am 'Add some feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Create a new Pull Request.

## Contact

For questions or feedback, please contact [@Bhavyansh03-tech](https://github.com/Bhavyansh03-tech).

---
