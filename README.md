![Public Sector Accelerators logo](/docs/Logo_GPSAccelerators_v01.png)

# Text-to-Speech for OmniScript and Flow

[Required. Show overview of the Accelerator. This should match the approved content used on the Accelerator listing.]

Accelerator Listing: [insert url to the public listing on the Accelerator site](https://gpsaccelerators.developer.salesforce.com/) (tbd once published)


## Description

This component takes Text as an input and converts it into an Audio file for playback.  There are many situations where this might be useful.  For example, this could be used to generate an audio recording indicating exactly what benefits an applicant is eligible.  

The component can be used in an Omniscript or in a Flow.  It could even also be used on a Lightning record page.  There is a single input that can take text as either literal values or variables and placeholders from Omniscripts and Flows.  



## Included Assets

This Accelerator includes the following assets:
<ol>
  <li>An <strong>unmanaged package</strong> (link below; metadata is also found in the /force-app/main/default/ folder) that includes:
    <ul>
      <li>Apex classes</li>
      <ul>
        <li>TextToSpeechGetAudio - Used by the textToSpeech LWC to perform the API call to VoiceRSS</li>
        <li>TextToSpeechGetAudio_TGN_TEST - Test class for TextToSpeech Apex class</li>
      </ul>
      <li>Custom Metadata</li>
      <ul>
        <li>TextToSpeech - Used to store metadata such as the API Key, Country Code, and Voice for the TextToSpeech Component</li>
      </ul>
      <li>Remote Site</li>
      <ul>
        <li>VoiceRSS - Remote Site Setting used to access https://api.voicerss.org</li>
      </ul>
      <li>Lightning Web Component (LWC) </li>
      <ul>
        <li>textToSpeech - LWC that is added to Omniscript or Flow to convert text to audio</li>
      </ul>
    </ul>
  </li>
  <li><strong>OmniScripts</strong> located in the /datapacks/ folder</li>
  <ul>
    <li>Example Text to Speech Omniscript - This is a basic Omniscript example that demonstrates the TextToSpeech cabilities.  There is a simple text input which is then spoken by the TextoSpeech component</li>
  </ul>
  <li><strong>Documentation</strong>, including:
    <ul>
      <li>This readme file</li>
    </ul>
  </li>
</ol>


## Before You Install

* The Omnistudio Managed Package must be installed
* This accelerator uses <a href="https://www.voicerss.org/">VoiceRSS</a> as the service that converts text to speech.  You will need to obtain an API key for VoiceRSS to use this accelerator. VoiceRSS offers a free tier that supports up to 350 conversions a day.  Click <a href="https://www.voicerss.org/login.aspx">here</a> to signup for an API key

**License Requirements** 
* License Public Sector Solutions - requires Foundations or Advanced for internal; requires Communities for external

**Accelerator or Technology-Specific Assumptions** 
* You have installed and configured OmniStudio and provided permission to PSS objects.
* Lightning Web Security must be enabled under Setup → Session Settings

**General Assumptions** 
* You are using this Accelerator in a sandbox or test environment. It is recommended that you not install any Accelerator directly into production environments.
* Example: If you do not have a Salesforce org licensed to you, you may try Public Sector Solutions for free with one of our [trial environments](https://developer.salesforce.com/free-trials/comparison/public-sector).
* You are using this Accelerator in conjunction with the Salesforce Lightning Experience (LEX) - not the Classic UI.


## Installation

Install the TextToSpeech package from this location:  https://login.salesforce.com/packaging/installPackage.apexp?p0=04tal000000r3Cf
* Click the Yes checkbox on the  grant access to these third-party web sites popup


## Post-Install Setup & Configuration

* Add Apex Class Access to the TextToSpeechGetAudio Apex Class for any profiles or permission sets that will uses this function.  This includes Community users.
* Signup for a VoiceRSS API Key <a href=https://www.voicerss.org/login.aspx>here</a>
* Go to Setup → Custom Metadata Types
* Find and click on TextToSpeech
* Click the ManageTextToSpeech button
* Click the Edit link next to APIKey and paste in the API key value in the Value field
* Click the Save button
* Note also that in the Custom Metadata you can set values for the Voice and  Country Code.  
  * Valid values can be found <a href=https://www.voicerss.org/api/>here</a>

<b>Configuration</b><br>
To add to an Omniscript
* Drag a Custom Lightning Web Component Input element onto the Step of the Omniscript where the Text To Speech will occur
* Select textToSpeech for the Lightning Web Component name
* Under Custom Lightning Web Component properties set Property Name to inputText and Property Source to the value you want spoken.  This could be literal text or a placeholder value derived from a Set Value, Dataraptor element or a formula element
  ![Omniscript Config Screenshot](/docs/FlowConfigScreenshot.png)


To add to a Flow
* Add a Screen element to the Flow
* On the Components tab, search for the textToSpeech component and drag the component onto the screen element
* Set the API name of the component.  The specific value entered does not affect how the component works
* Enter the value to speak in the Text To Speak field.  This can be a string or it could be a variable
  ![Flow Config Screenshot](/docs/OmniscriptConfigScreenshot.png)



## FAQs


**_Q: Can this accelerator be used with other translation services like Amazon’s Polly, Google’s Text to Speech or ChatGPT ?_**

A: This accelerator is specifically configured to work with VoiceRSS's API however this is an accelerator and coding changes could be madke to the textToSpeech LWC and the TextToSpeechGetAudio Apex class to work with other translation services.  

**_Q: What are the limitations of the free tier of VoiceRSS ?_**

A: VoiceRSS offers a free tier of translations with up to 350 requests per day.  More information about VoiceRSS can be found <a href="https://www.voicerss.org/pricing/">here</a>

**_Q: I can see the component in my Omniscript but no audio is played ?_**

A: Check to make sure that you have signed up for a VoiceRSS API Key and you have updated the Custom Metadata to point to this API key.  The package does not install a valid VoiceRSS API Key

**_Q: Why is the Text To Speech component just saying the work "null" in an Omniscript  ?_**

A: This can happen if the inputText property of the Text to Speech Lightning Web Component is not valid.  Check to make sure that the the Text to Speech Lightning Web Component's inputText property is set to either a literal value or if it is an element that the element is enclosed in %.  Also if you are using a Text element from the Omniscript that you are referencing the complete path including the Step name in the expression.  Also make sure that if you are using a Set Value that the Set Value element name is not the same name as the Custom LWC's name.  See the example Omniscript for a working example.


## Revision History

[Required. High level description of the Accelerator's versions, with the date it was made publicly available. If more detailed release notes or change log are necessary, create a separate readme in the same folder and link to it from here.]
<strong>1.0 Initial release (31 Auf 2024)</strong> - Initial Release



## Terms of Use

[Required. Cleared terms of use.  This must match the approved content used on the Accelerator listing.]

Thank you for using Global Public Sector (GPS) Accelerators.  Accelerators are provided by Salesforce.com, Inc., located at 1 Market Street, San Francisco, CA 94105, United States.

By using this site and these accelerators, you are agreeing to these terms. Please read them carefully.

Accelerators are not supported by Salesforce, they are supplied as-is, and are meant to be a starting point for your organization. Salesforce is not liable for the use of accelerators.

For more about the Accelerator program, visit: [https://gpsaccelerators.developer.salesforce.com/](https://gpsaccelerators.developer.salesforce.com/)
