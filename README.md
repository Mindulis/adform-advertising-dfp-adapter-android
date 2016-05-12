# Introduction

The Adform DFP adapter can be used to integrate Adform ads into the Google Mobile Ads mediation platform.

# Integration

## Getting started

1. If you haven't integrated the Google Mobile Ads SDK, please do so, you could find documentation [here](https://developers.google.com/admob/android/quick-start).
2. You need to import Adform Advertising SDK to your project. Instructions on how to it you can find [here](https://github.com/adform/adform-android-sdk/wiki/Getting-Started).
3. Download our DFP adapter library and include into your project. You could download it from [here](https://github.com/adform/adform-advertising-dfp-adapter-android/raw/master/AdformDfpAdapter.jar).         
4. Then you have to configure banner or interstitial custom event in DFP interface. More information on how to do so you can find [here](https://developers.google.com/mobile-ads-sdk/docs/dfp/android/custom-events). There are two very important steps when defining a custom event:

	* You must set master tag id provided by Adform in parameter field.
	* You must use `com.adform.dfp.AdformBannerAdapter` class for inline ads and `com.adform.dfp.AdformInterstitialAdapter` class for interstitial ads (class name field).

## Passing additional parameters to Adform banners

Additionally you can pass key values to mediated Adform banners. 

When creating the AdRequest for an AdMob interstitial create an Android Bundle object with your keyvalues as extras (see example below). Add your custom Bundle to the AdRequest using `addCustomEventExtrasBundle(<adform adater class>, <var name for your bundle>)`

```java
 	Bundle bundle = new Bundle();
    bundle.putString("age", "41");
    PublisherAdRequest publisherAdRequest = new PublisherAdRequest.Builder()
            .addCustomEventExtrasBundle(AdformBannerAdapter.class, bundle)
            .build();

