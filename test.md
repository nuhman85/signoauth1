# signoauth1

<dependency>
				<groupId>com.github.seratch</groupId>
				<artifactId>signedrequest4j</artifactId>
				<version>2.14</version>
			</dependency>
      
      
      
      package com.mgiorda.oauth;

import com.github.seratch.signedrequest4j.OAuthAccessToken;
import com.github.seratch.signedrequest4j.OAuthConsumer;
import com.github.seratch.signedrequest4j.SignatureMethod;
import com.github.seratch.signedrequest4j.SignedRequest;
import com.github.seratch.signedrequest4j.SignedRequestFactory;

public class TestClass {
    public static void main(String[] args) {

        OAuthConfig oauthConfig = new OAuthConfigBuilder("myApiKey", "myApiSecret")
                .setTokenKeys("myAccessKey", "myAccessSecret")

                .build();

        OAuthSignature signature = oauthConfig.buildSignature(HttpMethod.GET, "http://serviceUrl")
                //.addQueryParam("aParam", "aValue")
                //.addFormUrlEncodedParam("myParam", "anotherValue")
                .create();

        System.out.println(signature.getAsHeader());
        System.out.println(signature.getAsHeader());

        OAuthConsumer consumer = new OAuthConsumer("xhufavtho35txajjl0foedi5", "ztgid9u58c");
        OAuthAccessToken accessToken = new OAuthAccessToken("token", "token_secret");
        SignedRequest threeLeggedOAuthRequest = SignedRequestFactory.create(consumer, accessToken);


        SignedRequest signedRequest = SignedRequestFactory.create(consumer, SignatureMethod.HMAC_SHA1);

        String Url = "https://openapi.etsy.com/v2/oauth/request_token";
        com.github.seratch.signedrequest4j.HttpMethod method = com.github.seratch.signedrequest4j.HttpMethod.GET;
        String nonce = "k33F34WiKtx";
        long timestamp = 1594771641L;
        String signatures = signedRequest.getSignature(Url, method, nonce, timestamp);

        //signedRequest.setRsaPrivateKeyValue("-----BEGIN RSA PRIVATE KEY-----\n...");

        System.out.println(signatures);


    }

}
