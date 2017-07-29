# duphlux-javascript-lib
Javascript inline implementation. No redirects, perform authentication on same page.


## Implementation

Implementing Duphlux JS is a simple process. 

First add a line of client-side code. We recommend adding it as the first script on your page.

```
<script src="https://duphlux.com/webservice/js/inline.js"></script>
<!-- add your other scripts below -->

```

## Usage

Once you've added our script to your page, you can launch duphlux by adding a simple button as shown below.

```
<button type="button" onclick="launchDuphlux()"> Launch </button>

<script type="text/javascript">
    function launchDuphlux() {
        DuphluxPop.init({
            token: '[YOUR-APP-TOKEN]', // This is found under your app in your dashboard.
            timeout: 900, // timeout in seconds
            phone_number: "[PHONE-NUMBER-TO-AUTHENTICATE]",
            redirect_url: window.location.href, // Or any custom url of your choice
            transaction_reference: [TRANSACTION-REFERENCE], // A unique transaction reference to identity this authentication request
            callback: function () {
                return {
                    ## Called on a successful authentication. We pass back your unique transaction reference.
                    onSuccess: function (reference) {
                        alert("Success: " + reference); // Handle this event your own way
                    },
                    ## Called when an authentication fails. We pass back your unique transaction reference.
                    onFailure: function (reference) {
                        alert("Failed: " + reference); // Handle this event your own way
                    },
                    ## Called if we encounter any duphlux related errors. We pass the error message encountered.
                    onError: function (errorMessage) {
                        alert("Error: " + errorMessage); // Handle this event your own way
                    }
                }
            }
        });

        // Now launch the Duphlux authentication process
        DuphluxPop.launch();
    }
</script>

```
That's all!!

Please see our documentation page for all possible parameters to pass on init.