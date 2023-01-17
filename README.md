# Адаптер Yabbi для AppLovin

## Установка SDK AppLovin
Установите **AppLovin Unity Plugin** следуя официальной  [документации](https://dash.applovin.com/documentation/mediation/unity/getting-started/integration).

## Установка адаптера YabbiAds
Загрузите **AppLovinYabbiAdsAdapter**. Он включает в себя последнии версии Android и iOS Yabbi SDK.  
Версию для скачивания вы можете найти по ссылке - [клик](https://github.com/YabbiSDKTeam/applovin-unity-adapter/releases).

## Настройка External Dependency Manager

External Dependency Manager уже включен в плагин.
Для разрешения конфликтов зависимостей в вашем приложении выполните следующие шаги:

1. После импорта плагина в редакторе Unity выберите File → Build Settings → Android.
2. Добавьте флаг Custom Gradle Template для Unity 2018.4 - Unity 2019.2 версий или Custom Main Gradle Template для Unity 2019.3 или выше (Build Settings → Player Settings → Publishing settings).
3. Добавьте флаг Custom Launcher Gradle Template (Build Settings → Player Settings → Publishing settings).
4. Включите настройку - "Patch mainTemplate.gradle" (Assets → External Dependency Manager → Android Resolver → Settings).
5. Включите настройку - "Use Jetifier" (Assets → External Dependency Manager → Android Resolver → Settings).
6. Добавьте следующий код в launcherTemplate.gradle
```gradle
android {
   
    // другие настройки
        
    defaultConfig {
        
        // другие настройки
          
        multiDexEnabled true
    }
}
```
7. Затем выберите Assets → External Dependency Manager → Android Resolver и нажмите Resolve или Force Resolve.
8. Модули, которые необходимы для работы будут импортированы в mainTemplate.gradle вашего проекта.


**YabbiAds** поддерживает 2 типа рекламы
- Полноэкранный баннер - Interstitial Ad
- Полноэкранный видео баннер с вознаграждением - Rewarded Ad


## Interstitial Ad
> [Документация AppLovin](https://dash.applovin.com/documentation/mediation/unity/ad-formats/interstitials)

Для инициализации **YabbiAds** следуйте следующим инструкциям:
1. Установите параметры **Yabbi** с помощью метода **SetInterstitialExtraParameter**.
```csharp
 MaxSdk.SetInterstitialExtraParameter("id_блока_applovin", "yabbi_publisher_id", "YOUR_PUBLISHER_ID");
 MaxSdk.SetInterstitialExtraParameter("id_блока_applovin", "yabbi_interstitial_id", "YOUR_INTERSTITIAL_ID");
 MaxSdk.SetInterstitialExtraParameter("id_блока_applovin", "yabbi_rewarded_id", "YOUR_REWARDED_ID");
```
3. Замените **YOUR_PUBLISHER_ID** на ключ издателя из [личного кабинета](https://mobileadx.ru).
4. Замените **YOUR_INTERSTITIAL_ID** на ключ соответствующий баннерной рекламе из [личного кабинета](https://mobileadx.ru).
5. Замените **YOUR_REWARDED_ID** на ключ соответствующий видео с вознаграждением из [личного кабинета](https://mobileadx.ru).

6. Реклама **YabbiAds** готова к показу, используйте метод **LoadInterstitial**, для загрузки рекламы.
```java
MaxSdk.LoadInterstitial("id_блока_applovin");
```

## Rewarded Ad
> [Документация AppLovin](https://dash.applovin.com/documentation/mediation/unity/ad-formats/rewarded-ads)

Для инициализации **YabbiAds** следуйте следующим инструкциям:
1. Установите параметры **Yabbi** с помощью метода **SetRewardedAdExtraParameter**.
```csharp
 MaxSdk.SetRewardedAdExtraParameter("id_блока_applovin", "yabbi_publisher_id", "YOUR_PUBLISHER_ID");
 MaxSdk.SetRewardedAdExtraParameter("id_блока_applovin", "yabbi_interstitial_id", "YOUR_INTERSTITIAL_ID");
 MaxSdk.SetRewardedAdExtraParameter("id_блока_applovin", "yabbi_rewarded_id", "YOUR_REWARDED_ID");
```
3. Замените **YOUR_PUBLISHER_ID** на ключ издателя из [личного кабинета](https://mobileadx.ru).
4. Замените **YOUR_INTERSTITIAL_ID** на ключ соответствующий баннерной рекламе из [личного кабинета](https://mobileadx.ru).
5. Замените **YOUR_REWARDED_ID** на ключ соответствующий видео с вознаграждением из [личного кабинета](https://mobileadx.ru).

6. Реклама **YabbiAds** готова к показу, используйте метод **LoadRewardedAd**, для загрузки рекламы.
```java
MaxSdk.LoadRewardedAd("id_блока_applovin");
```