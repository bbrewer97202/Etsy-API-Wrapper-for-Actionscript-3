An Actionscript 3 class that wraps the Etsy.com V1 API.

Last updated: March 13, 2009 to reflect "03-09-05" Etsy API updates

Example:

    import com.thunderfarm.etsy.api.EtsyAPIRequest;
    import com.thunderfarm.etsy.api.EtsyAPIRequestEvent;	

    var etsy:EtsyAPIRequest = new EtsyAPIRequest(YOUR_API_KEY);
    etsy.addEventListener(EtsyAPIRequest.COMPLETE, onRequestComplete);
    etsy.getUserDetails(SOME_USER_ID, { detail_level: "high" });	

    private function onRequestComplete(event:EtsyAPIRequestEvent):void {
        trace("status: " + event.httpStatus);
        trace("results: " + event.results);
        trace("text: " + event.text);
    }
	
This code makes a /users/USER_ID call, then handles the response in the onRequestComplete method. The event object passed contains three properties of potential use:

1. _status:_ integer with the http status of the request. See Etsy API documentation for full explanation. In the event of an unknown error, a Flash IO error, or a Flash security error, this value is set to zero.
2. _results:_ string with raw JSON response. If the request was unsuccessful, this will be null.
3. _text:_ string with any message that comes with the response. If successful request, this will be empty. If the request resulted in an error, this contains the error message.

There is much still to be done on this, including significant testing. 