# DaggerViewModel

## Usage

```groovy
allprojects {
  repositories {
    maven { url 'https://jitpack.io' }
  }
}

dependencies {
        compile 'in.nerd-is:daggerviewmodel:0.2.1'
}
```

This library depends on [dagger.android](https://github.com/google/dagger) and Jetpack's ViewModel.

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
