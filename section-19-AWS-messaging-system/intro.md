# Introduction to Messaging system
There are 2 common pattern of application communication, synchronous & asyncrhonous.
<img width="992" alt="image" src="https://github.com/user-attachments/assets/8d79b5a0-901a-4b6c-b8d9-b5ac4810d9bd" />

What if we need suddenly encode 1000 of videos but usually it 10? If using sync communication then our app will be overloaded and couldn't handle the requests. But if we are using async communication, then we can like limit the video processing one by one which will make our application still running.
That term is `decouple`, and in AWS we can use SNS (pub/sub), SQS (queue), and Kinesis (real-time streaming), and those services highly scaleable 
