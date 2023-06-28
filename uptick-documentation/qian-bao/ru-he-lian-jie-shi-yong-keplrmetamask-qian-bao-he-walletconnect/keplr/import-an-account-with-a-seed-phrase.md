# Import an Account with a Seed Phrase

1. In the initial pop-up window, choose **Import Existing Account**

* If you have used Keplr before, click on the silhouette in the upper-right corner, then the blue box labeled **Add Account**, and select **Import Existing Account**
* ![](<../../../.gitbook/assets/image (3).png>)![](<../../../.gitbook/assets/image (1).png>)

2. Enter your mnemonic/seed phrase/private key in the appropriate slot, separating the words with spaces and taking care to check they are spelled correctly
3. Make sure you have imported the account with the correct derivation path, viewable by clicking on **Advanced**

* Normally, the derivation path should be `m/44'/…’/0/0/0`, but if you see that importing the account via mnemonic on Keplr, the Cosmos Mainnet address displayed is different than yours, it is possible the derivation path ends with 1 (or another number) instead of 0
* If this is the case, you just have to start the process over, and replace the last 0 with 1
* Learn more in the [Keplr FAQ](https://faq.keplr.app/)

4. If you have not used Keplr before, set a **strong** password for the Keplr extension, and click **Confirm**
