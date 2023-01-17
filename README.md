# Адаптер Yabbi для AppLovin

## Шаг 1. Установка SDK
Установите **AppLovin Unity Plugin** следуя официальной  [документации](https://dash.applovin.com/documentation/mediation/unity/getting-started/integration).

Для добавления рекламной сети **YabbiAds** следуйте инструкции по добавлению кастомной рекламной сети - [клик](https://dash.applovin.com/documentation/mediation/android/mediation-setup/custom-sdk)


Для добавления адаптера **YabbiAds** следуйте иснтрукциям ниже:
1. Перейдите в файл **Dependencies.xml** расположенный в папке **Assets/MaxSdk/AppLovin/Editor/Dependencies.xml**.
2. Добавьте зависимость в файл.

```
<?xml version="1.0" encoding="utf-8"?>
<dependencies>
    <androidPackages>
    
       <!-- Другие зависимости AppLovin -->
       
        <!-- Добавьте зависимость -->
        <androidPackage spec='me.yabbi.ads.adapters:applovin+'/>
        
        <!-- Добавьте репозиторий для зависимости -->
        <repositories>
            <repository>https://mobileadx.ru/maven</repository>
        </repositories>
        
    </androidPackages>
    <iosPods>
    
        <!-- Другие зависимости AppLovin -->
        
    </iosPods>
</dependencies>

```


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