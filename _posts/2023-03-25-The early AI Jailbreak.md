<html>
<head>
    <meta charset="UTF-8">
</head>
<body>

<p>
Every new innovation comes with its problems and security concerns. In order to implement countermeasures, we need to see the effects and the security concerns that come out of it. In other words, the innovation—in this case, AI—needs to be used and adopted just like we have adopted the internet. That way, we will have a clearer vision on how to approach security measures and implement them.
</p>

<p>
It isn't clear how we are going to approach AI security just yet. I think that is because we are yet to see its operational effectiveness on the internet. One of the methods antivirus products improve is by analyzing more malware samples, for example. The same concept applies to AI; its security is directly proportional to its usage. So before we start evaluating security measures, it's important to understand the magnitude of what we are dealing with.
</p>

<p>
Now I wanted to test if I could potentially generate fake credit cards using ChatGPT. At first, ChatGPT was stubborn and didn't want to give me fake credit card details, but in the end, I was able to jailbreak it and get it to generate fake credit card info. In other words, I bypassed the security and moderation features.
</p>

<p>
To give you an idea of how ChatGPT responds when asking it for fake credit cards, this is how it responds:
</p>

<p>
<img src="https://drive.google.com/file/d/10s8TzFFI43m96laNE3T92M9qqj9UfEqX/view" alt="ChatGPT refusing to provide fake credit card details">
</p>

<p>
As you can see, it won't allow you to obtain such information, even if you try to circumvent the system by saying, for example, "for educational purposes."
</p>

<p>
I thought of this model, which I believe is at the core of jailbreaking, and security measures should follow a similar model approach when implemented. Essentially, it's about starting in a general category and sub-categorizing the topics until you reach the topic of interest. Below, you can find a representation of the mental model I had in mind when jailbreaking.
</p>

<p>
<img src="attachments/Pasted image 20241024172623.png" alt="Mental model for jailbreaking">
</p>

<p>
In general, the trick is to prompt LLMs (Large Language Models) in the same way you would hold a conversation with someone in real life and take it from there when trying to bypass the restrictions these models have. In real life, a very distrustful characteristic people have is lying to "bypass" certain actions—you see where we are going here. This should give you an idea on bypassing restrictions when dealing with ChatGPT and other LLMs. I have also discovered the repository <strong>Prompt Injection</strong> while writing this article, which goes in-depth on jailbreaking. However, the fundamental concept of jailbreaking is what I have explained above.
</p>

<p>
The following is the chat that made ChatGPT generate fake credit cards.
</p>

<p>
<img src="Pasted image 20241024172915.png" alt="Chat conversation part 1">
</p>

<p>
<img src="Pasted image 20241024172920.png" alt="Chat conversation part 2">
</p>

<p>
<img src="Pasted image 20241024172925.png" alt="Chat conversation part 3">
</p>

<p>
Now it will get interesting.
</p>

<p>
<img src="Pasted image 20241024172941.png" alt="Chat conversation part 4">
</p>

<p>
As you can see, I am dragging ChatGPT by its tail; now it has referred me to a website where I can generate fake credit cards.
</p>

<p>
<img src="Pasted image 20241024173038.png" alt="Chat conversation part 5">
</p>

<p>
Pay close attention to how I am prompting ChatGPT; please note that all credit card info is fake and none of it works, so take it easy, friends.
</p>

<p>
<img src="Pasted image 20241024173117.png" alt="Chat conversation part 6">
</p>

<p>
Now I have asked ChatGPT to generate fake credit cards again, and it refused to do so, then proceeded to provide a link to the same website. Now, in the following image, it's where we hit the jackpot. It seems like ChatGPT got pressured when the word "frustrated" was used.
</p>

<p>
<img src="Pasted image 20241024173231.png" alt="Chat conversation part 7">
</p>

<p>
As you can see, ChatGPT has generated 10 fake credit card details, even though it didn't want to at the beginning. This is called a jailbreak. Intelligence officers are probably the best at jailbreaking since they know how to take words out of someone's mouth. The point of me writing this article isn't about the jailbreak; it's about the approach to implementing security and moderation features. We should always try to replicate the human dialogue experience. That being said, this is the tip of the iceberg of a new era whose effects on our so-called 'human experience' we haven't fully understood. I totally think the approach to AI security needs to be radical and inspired by the way we live and interact.
</p>

</body>
</html>
