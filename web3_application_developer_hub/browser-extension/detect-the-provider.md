# Detect the provider

If you [use the `@metamask/detect-provider` module](https://docs.metamask.io/wallet/get-started/detect-metamask/#use-metamaskdetect-provider), it reliably detects both the mobile and extension provider. If you don't use `@metamask/detect-provider`, you must detect the mobile provider manually. You can manually detect the mobile and extension provider with the following code:

```
if (window.ethereum) {
  handleEthereum();
} else {
  window.addEventListener('ethereum#initialized', handleEthereum, {
    once: true,
  });

  // If the event is not dispatched by the end of the timeout,
  // the user probably doesn't have MetaMask installed.
  setTimeout(handleEthereum, 3000); // 3 seconds
}

function handleEthereum() {
  const { ethereum } = window;
  if (ethereum && ethereum.isMetaMask) {
    console.log('Ethereum successfully detected!');
    // Access the decentralized web!
  } else {
    console.log('Please install MetaMask!');
  }
}




```
