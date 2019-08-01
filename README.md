# DaggerViewModel

## Usage

This library depends on [dagger.android](https://github.com/google/dagger) and Jetpack's ViewModel. You should know how to use dagger.android and ViewModel first.

```groovy
allprojects {
  repositories {
    maven { url 'https://jitpack.io' }
  }
}

dependencies {
    implementation 'in.nerd-is:daggerviewmodel:0.2.1'
}
```

```kotlin
@Module
abstract class ViewModelFactoryModule {
  @Binds
  abstract fun bindViewModelFactory(factory: DaggerViewModelFactory): ViewModelProvider.Factory
}
```

```kotlin
@Singleton
@Component(modules = [
  AndroidInjectionModule::class,
  ViewModelFactoryModule::class
])
interface AppComponent {
  fun inject(app: ThisApp)
}
```

In Activity or Fragment:
```kotlin
@Inject
lateinit var vmFactory: ViewModelProvider.Factory

private val viewModel by lazy(LazyThreadSafetyMode.NONE) {
  ViewModelProviders.of(this, vmFactory)[YourViewModel::class.java]
}
```
