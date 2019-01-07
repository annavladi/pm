
**Ethereum Core Devs Meeting 52**
*Meeting Date/Time: Friday 4 January 2019 at 14:00 UTC*
[Recording](https://youtu.be/iSc3TbjZu1k)

**Agenda**

1. Testing Updates
2. Client Updates
  * Geth
  * Parity Ethereum
  * Aleth/eth
  * Trinity/PyEVM
  * EthereumJS
  * EthereumJ/Harmony
  * Pantheon
  * Turbo Geth
  *  Nimbus
  * Mana/Exthereum
3. Research Updates
4. Working Group Updates
* State Rent
* EWasm
* Pruning/Sync
* Simulation
5. Constantinople HF Evaluation
6. Roadmap
7. ProgPoW HF Decision(s)
8. Istanbul HF Roadmap

Attendees:
* Anna Vladi
* Hudson Jameson
* Pawel Bylica
* Adam Schmideg
* Afri 5chdn
* Alex Beregszaszi
* Alexey Akhinov
* Andrea Lanfranchi
* Daniel Ellison
* Danno Ferrin
* Danny
* Dimitry Khoklov
* Dimitri Harmany
* Greg Colvin
* Jacek Sieka
* Kalarabe
* Lane Rettig
* Martin Swende
* Meredith Baxter
* Miss If
* Mr Else
* Murat

Hudson: [00:13:57] Hello everyone and welcome to episode fifty-two of the core developer meetings. I'm Hudson and let's get to the agenda first. We're gonna have a quick announcement about note taking and to get in bounty associated with it so I'll have lane go over that. 

Lane: [00:14:19] Awesome thank you Hudson can you hear me clearly. 

Hudson: [00:14:21] Yes cool. 

Lane: [00:14:24] Welcome everybody happy new year super excited to kick off this year in fine health. So I'd like to introduce everyone to Anna who's on the call. Hudson mentioned I think our last meeting about a month ago that we were kicking off an initiative to help to have some to bring in some sort of external project management talent to help us just sort of run these meetings and just coordinate hard forks and things. Afri also kindly volunteered to help out with that process. And one of the things as you guys know I've been taking notes for these calls for most of 2018. So we're going to. So we're going to sort of experiment a bit going forward with that. So Anna has kindly offered to take notes for the meeting today. And the other piece of this is that we also set up a Gitcoin fund some massive thank you to Gitcoin for helping us out with this and for funding the first bounty. And so there's actually gonna be a bounty for note taking this is something that we hope to keep doing for all of these calls basically. So we may have some other fresh faces joining us to take notes going forward. Thank you. 

Hudson: [00:15:28] Yep. Exactly. And we also have Murat in here. He is also part of the group of people who are kind of right now called like a project management group for the core devs which is a group of about. How many people something around seven or eight people who want to kind of learn how to navigate around either the EIPs or the core dev meetings or note take or help out in some way or another may maybe hard for coordination stuff like that. And Afri is he is going to be leading the hard for coordination path between now and the next part or after Constantinople. But also I guess leading up to Constantinople usually that role was taken by either no one. Or kind of taken by me for previous hard forks but he's stepped up to take that. So thank you so much Afri. And during calls for a hard fork related stuff I'll probably have Afri cover a lot of that. So just a heads up to everybody. I think that's about it on that topic. Let's go ahead and start with the testing updates. Is Dimitiri here. Yeah Dimitri's in here. Let me meet my phone. Dimitri if you want to go ahead take it away. 

Dimitriy Khoklov: [00:16:53] 
* Go client is working on a hive on the main net. 
* Go client fails on the 90 tests out of all of our test pool looks to be configuration errors or maybe high script errors
* Parity is still being integrated into the hive. 

Martin: [00:18:37] 
* 23 tests are failing on Parity now out of 21000

Dimitriy Khoklov: [00:19:12] 
* we need at least two clients work working on those tests so it could compare results to make sure that every issue you see in the hive is not a major issue. working on this next week

**Client Updates**
**Geth** 

Martin: [00:20:22] I was actually open. Peter would be on I will ping him to see . 

**Parity**

Afri: [00:20:40] 
* working on ProgPOW. I think we are up to date with the current spec and we are ready for ProgPOW on test net. 
* started looking in addition PWASM on EWAS The goal was eventually to join. EWASM test net.
* we stopped working on implementing fast synchronization. we want to have a hybrid of past what synchronization and future and implementing fast sync is one of the first steps process 
* started looking into removing accounts from parity in general account management and transaction signing should not be part of it. 
* we're trying to figure out how to transition  

**Nimbus**

Jacek: [00:22:10] Well holiday so not much progress to report 

Hudson: [00:22:22] Thanks great. Alef. 

[00:22:28] I don't have any update related to Constantinople. So yeah nothing to report. 

**Pantheon** 

Meredith: no update

**Mana**
* no update

**TurboGeth**

Alexey: [00:23:01] Hello. 
* working on reverse disk for the the history it's going to be quite important for the two TurboGeth to support light clients and snapshots. It will be part of ether mint.

**Swarm** 

Adam: [00:24:04] 
*  working on stability, some issues, working on fixing it. So we are expecting a stable swarms soon that's it. 

**EWASM** 

Alex Beregszaszi: [00:24:44] 
* Eth1X working group which proposes to introduce Pre-compiles using EWASM on the main net,proposal was made public a month ago. He proposed a couple of new pre-compiles the good thing I can report is most of those we have implemented in Rust of the new proposed weakened price. And the reason we implemented them to have them benchmarked and to also run metering different metering strategies on them to come up with the good solution. So after we implemented them we also focused on creating a benchmarking framework to benchmark all these pre compiles. We haven't done benchmarking every single one yet but at least we have a framework which should allow benchmarking different implementations and the won't be focused on is benchmarking different implementations of Shard 2 5 6 and running different and metering strategies on them. So all this can be found on the EWASM or on github and did a benchmarking repo and the second focus area was the test net the public test that we have we worked quite a bit to improve the documentation and the documentation covers things like how to use the test net and how to compile and deploy contracts. And the second part is where we did a lot of improvements. And we should have much better description haw to work with C or Rust contracts. We also have decided to call it WASM chisel which can basically fix any kind of wasn't binary to be compatible with WASM. And that's coming to a release soon. And that should enable different languages to be used on the test net. Last note on the test set itself. So far the test net was written in go ethereum and C++ VM called Hera but in the last couple of weeks we also deployed a purely Go implementation called Requim on the test net so we have 2 implementations of Web assembly VM is running the test net for the last couple of weeks and it was running without any issues. So I think that shows that it should be possible. What Afri mentioned to have parity also join the test net without any issues sometime in the future. The next thing I wanted to mention is have you working on on service regarding blockchain platforms using web assembly and sort of reveal. Look at how they use Web assembly while not only platforms which is web assembly with others which use some other VM similar or dissimilar to Q2 of assembly. But of course the main main focus is on the assembly itself and we intend to include best practices we have found and to service should be published. I think that's it. 

**Ethereum J**

Dmitrii (Harmony): [00:28:15] 
* working on pass all github tests that were added by Dmitri and other contributors for Constantinople
* found 1 bug with the compiler Maddox all others were related to empty storage account 
* we are ready for the fork  
* we are not running on a hive, we had issues with it, not fixed yet 

**Ethereum JS**

Alex Beregszaszi: [00:29:11] 
* The first part is the LP library which has been written to TypeScript and that has been published before Christmas and that work is being done on rewriting other libraries to typescript.  

**Trinity**
not present

**Research**

Danny: [00:30:21] 
* focusing on refining this stage zero spec for a Serenity where Phase Zero is the core prove of stake chain. 
* We are moving into a relatively stable place. 
* We're still refining optimizations. 
* Need spec peer review and to provide feedback in the next 2-3 weeks

**Working Groups**

Alexey: [00:32:22] 
* split the spec into much smaller pieces which I probably would call cards. 
* working on Alternative proposals to stem the steady growth. stem the state growth while increasing the block size limit. Post is [here](https://ethereum-magicians.org/t/on-raising-block-gas-limit-and-state-rent/2249) 
* also wrote up the [proposal](https://ethereum-magicians.org/t/backwards-forwards-sync-of-ethereum-clients/2258) for the backwards forwards sync  

Hudson: [00:36:16] Great. And you mentioned the meeting later this month. There is an off very optional in-person meeting January 26 to 28 in the San Francisco Bay Area of the United States was discussed on a previous call and also some people are on a an email list for that. If you're not on the email list reach out to me on Twitter and give me your email and I will agree to the list if you're interested in possibly attending. We're also going to try to have remote options for parts of it or not as much of it as we can. I'm not primarily in charge of that. That's pretty much something that consensus has graciously volunteered to kind of take on. And this stemmed from the ad hoc meetings at DEVCON. I believe so. Again, just reach out to me and we don't have a specific venue yet. As far as I can tell but that'll be coming up pretty soon we'll have information on that and send me your email if you're interested it looks like a Peter. Or actually was there any questions about that before I start or get to just throw it to Peter. 

Alexey: [00:37:36] Oh actually can I just add very quick. Another update I forgot to say. I have found another person to help me with this kind of tasks. And so he's going to join me at the end of January and he's also going to be coming to that to that meeting as well to to get introduced to other people. So I've been working with this person for a long time since in my three previous jobs. So I'm pretty kind of sort of relieved that there will be somebody helping me with that. 

Martin: [00:38:16] Awesome. Peter do I give an update on Geth. 

Karalabe: [00:38:22] Yes. My vacation was great. So not really. I mean I don't have any particular updates regarding forks or whatnot. One nice update is that about half a year ago we were working on pruning and we found we lost some fault and it took us an eternity to find it and it turned out that it simply was not our fault. And it was everything is actually working. So now we have a fresh energy to actually do pruning properly again. So that's it. That's good news but that's about it. 

Hudson: [00:39:06] And good we're on track here. Let's go ahead and go to the Constantinople hard fork that is currently in the works. Afri do you have the latest figures on when that's supposed to happen. I know you've been keeping up with that yes. 

Afri: [00:39:24] So let me check. I have a small script calculating the average time on remaining blocks and we are off by 10 minutes and trudges with seconds after 12:00p.m. UPC on Wednesday the 16th . We are very close to where we want to go. 

Hudson: [00:39:51] So one potential concern is that according to a Web site and I guess back in script running that Peter Pratcher setup from one of the major mining pools only around 11 percent of the nodes are on the latest versions of Geth or Parity that are compatible with Constantinople. Is that a concern?. And is that something that we should be proactive about as far as trying to get the messaging further. Does anyone have technical reasoning behind that I'm not smart enough. 

Afri: [00:40:29] I have two comments regarding the first one is a little bit out of scope for this call but we usually used to have blog posts on Ethereum.org Announcing hard forks and maybe we should consider this. I don't know anyone on this information professional to step up. 

Hudson: [00:40:47] Oh yeah. I usually do that and I forgot I do that. So I'll do that. 

Afri: [00:40:52] Yeah maybe this will have this like spreading the word. And the other thing we already discussed was. I think there are a lot of clients tracked by this fork are not on Ethereum because a lot of old nodes are not even updated And I expect them not to run on this main net. So I personally don't think this is a major issue but they are spreading about what something we should do with next two weeks. 

Hudson: [00:41:24] Or any other comments. 

Alexey: [00:41:26] So I thought of something else. Is that so. I know that Parity for example supports usually a kind of two versions one of the stable ones and another one and both of them are now Constantinople ready as far as I understand. But as with the other clients I guess as far as I understand it only has one version which sort of supports the Constantinople. I wonder if this is a might be the reason why you could see that a slower adoption rate slower upgrade rate for Geth because people are usually very sort of reluctant to go to straight away. So I just thought that was my thought when I looked at the stats. 

Karalabe: [00:42:11] We don't have so in Geth we kind of have two versions one of them are stable releases which are kind of release every two weeks and the other one is likely to say unstable but that is pretty much stable to but both of them are and have been on the Constantinople now for a very long time OK. 

Hudson: [00:42:38] OK. Any other comments.? OK. And the next item are actually I don't I don't think there's any other stuff on Constantinople we may have. Oh the next meeting we're gonna have it's gonna be post Constantinople so we'll just go to what we usually do and talk in the core devs chat if there's gonna be any problems or anything we need to do. 

Alexey: [00:43:09] Oh actually Hudson maybe it makes sense to have some kind of. Around the fork time maybe it makes sense to gather some like look like exceptional meeting or something were completely optional but just to. Talk through the what's going on if we if people want to do it assume sort of to monitor the transition. I don't know if it's helpful because that did actually kind of reaction time might be I don't know it doesn't make sense to anybody. 

Hudson: [00:43:40] Yeah. And this makes sense. I can set up the call and have people who want to join who are up at that time can definitely join. And it'll be a party. 

Lane: [00:43:55] That's why I was gonna say basically the best case scenario is no news and then we just celebrate. 

Hudson: [00:44:00] Yep totally. Yeah I'm up here. 

Martin: [00:44:03] I don't know. When if I mentioned, forkmon.eth.ops.io (verify link) 

Alexey: [00:44:10] Well we can watch the fork happen. l I think it would be also it would also be useful for people who run some important services to just get some real-time updates with some interpretation rather than just sitting and watching the like a fork monitor or something like this because people have a different sources of information. So if we can just throw it in and sort of explain everything as it happens. 

Hudson: [00:44:43] I can see if Infura or mycrypto and others want to join the people who run a lot of nodes. Be cool. And if you have ideas for other groups. Alexey just let me know who I can reach out to them. 

Karalabe: [00:45:03] By the way Martin regarding the fork monitor. Could you also add a pre Constantinople node to It would be nice to see what happens 

Hudson: [00:45:22] Let's see. What is next. I think we're going to just have a overview from offering on the Istanbul hard fork. That's going to be coming up after Constantinople including a rough proposed road map and just some other things about that so offer if you want to go over that yeah sure. 

Afri: [00:45:48] I was thinking about the stuff we had in mind for quite a while now. We wanted to have a fixed HF schedule. Protocol upgrades deployed on Main on a fixed schedule like every nine months or something like that. And I was running some numbers and proposing something I would just go through now. If we agree on this we would have the next main net HF in October so it would be nine months. I already saw there was some discussion to have a shorter maybe eight months or six months or someone proposed three months’ cycle. I don't think it should be too short but yeah, we should discuss what a reasonable cycle would be. I was running numbers against a nine-month cycle and this would mean we have the next hot fork I call it Istanbul. Next up on 16th of October 2019 its a Wednesday this means we should have a test net hard fork on Ropsten nor any other suitable test not around mid-August. If you want to follow this I put the dates on the agenda and you may comment. And most importantly we should have the deadline to accept proposals that go into this hard fought around mid-May. So we have around five months to properly implement and test or the protocol upgrades. That's a road map action item so we should decide how do we want this? We should decide what's a reasonable timeline. I personally have people having nine months and yes, any comments would be good. 

Hudson: [00:48:06] Yeah. That timeline was for the whole. The amount of length between today and the next HF right. ? 

Afri: [00:48:13] Exactly except this time from Constantinople to Istanbul. Exactly nine months. 

Greg Colvin: [00:48:17] Didn't We want to get ProgPOW in before that if possible.? 

Martin: [00:48:29] So yeah, I guess we haven't really decided about ProgPOW and that's so I mean I tentatively I kind of agree that it's sensible to go to work every nine months. But yeah, I'm also I also believe that we should roll out ProgPOW and I kind of feel that that's We should have a discussion about that. 

Hudson: [00:48:56] Yeah. I'm seeing things. Yeah. That was actually the next item but we can kind of start talking about that a little bit. And I'm kind of hearing two sides one of them is that we should have the ProgPOW fork if we're going to have that at all before nine months maybe sometime in between there. The other point of view is that we should have it at nine months and bundle it with a bunch of other updates. So I'm starting to read your notes on the agenda Afri was that was the ProgPOW mentioned on there. If we were to do it or is that just kind of being discussed now. 

Afri: [00:49:42] That's what I'm doing is proposing how to manage protocol upgrades on the main net. I'm not suggesting that we force also to fix a schedule. I mean I would recommend that we stick to a plan in general about the group whatever decides. We want to have an additional hard fork in between then Why not. But that's not relevant for my agenda item right now. So if we want to move to ProgPOW first let's just talk about no. 

Hudson: [00:50:12] Yeah let's do ProgPOW first and then we'll go back to the proposed rough timeline for Istanbul and some of the other EIPs and stuff we've been working on for this formal process for hard fork. So we have Mr If Mr. Ellis from the ProgPOW team. Thanks for coming back. You all and they can. Along with Martin and a few others probably give some updates on ProgPOW. Do You do you'll have any particular updates for the specification that hasn't already been covered by any of the devs here. 

Mr Else: [00:51:03] Sorry about that. Yeah. The changes that we published in early December there were two small changes one late November and one early December to try to. The first one made it a little bit harder for specialized days like a six to be made. The second one stabilized hash rates. Those are the only two small changes we've had. We don't see any changes going forward from there. 

Hudson: [00:51:35] OK now let's talk about implementation of the Gangnam test that first just a quick overview. As my understanding correct that the Gangnam test net is just a test step running client implementations of ProgPOW? 

Martin: [00:51:56] It started off with a fashion then switched to ProgPOW after 3000 blocks. 

Hudson: [00:52:03] Cool. And how's that going. I think Martin you posted something about it the other day in chat. What's what's the latest on all that.? 

Martin: [00:52:13] Yeah it's. Actually, I haven't kept track of it but it had some problems during the first epoch transition where one of the miners fell off I'm not sure about the specifics of whatever it was. It's been fixed I've heard. Does anyone know more details about.? 

Mr Else: [00:52:39] The original miner from the original do you miner had a bug that when you transitioned to epochs it would crash. It was just a cute programming bug that's been fixed and so we're up to 150 thousand blocks now. So, I've done multiple epoch transitions with no problems 

Martin: [00:53:03] The folks and we kind of from the from the outset we knew that the things that we need to do tests are basically the epoch transitions because those are the parts where you can trip fall and from my perspective yeah that's basically the big thing that needs to be testing. And regarding this should be bundled with other updates. That's my take is that the transition from Hashimoto to ProgPOW does not involve the EVM or state transition mechanics at all. It's only the envelope of the blocks and the current test. The extensive tests that we need to write for hard Folks we don't have to do those tests. There are other kinds of tests and they mainly the main thing to test is you know can we switch to a new DAG at a certain epoch. Does it work or not.? of course you know if clients can verify it but they're pretty straightforward tests and that's what I believe. There's no real point in bundling it with EVM updates. 

Hudson: [00:54:29] So I guess what we wanted to decide today is not necessarily when it would happen but if it would happen and then we can start to kind of formulate what that entails if we decide it's going to happen. I haven't heard much dissent as far as people saying they don't want it to happen. Very few. Just a couple of people. So, what are some opinions on whether or not this should go forward. Is there anyone who doesn't want this to go forward or. 

Martin: [00:55:06] No I just thought that some well opinions and facts about why I want it. So We know for a fact that there exists ASIC miners. So, it's obviously profitable to manufacture or buy and use ASIC miners. There is some the E3 7 that started as first generation ASIC miners but they're also second generation classic miners one from Bitmine which I'm not sure if it's even publicly released. And there's also some other companies that produce some ASIC miner for Ethereum. There is also a fact that there are FPGA based accelerators I mean my Minority sells them which evidently you can make a profit if you put them on your GPU and You can accelerate and we believe that ProgPOW is more ASIC resistance and also more resistant to those kinds of accelerators for the GPUs And yeah there is grounds to believe that switching to ProgPOW would postpone the ASIC level of ASICs in our network for at least a year probably been a lot more than that So we know today Ether hash hashimoto has flaws which are actively being targeted. That's why I would like to switch as soon as possible to give us more time to move to prove of stake 

Hudson: [00:57:01] OK. Do we have other opinions? 

Alexey: [00:57:05] Well I just wanted to remember Martin you also said in a previous call or something that the other side of this of course is that when if this such time comes they say you would postpone it for one year. But after that year because the ProgPOW is a bit more sophisticated than Et Hash then obviously making ASIC is much more difficult. But if somebody does manage to make it then they will have a very good advantage. And so that is kind of on the other side of the coin. So is that is that still is it still your know do you still believe that.? 

Martin: [00:57:47] I still believe that. I still believe that it's. About a year after with this to ProgPOW we hear new rumors about plastics being manufactured some really large player has the monopoly of the ethereum ASICs. Then yes, we should probably consider switching to something which is trivially trivial to implement in hardware. 

Mr Else: [00:58:15] So I wouldn't I wouldn't interject a bet that the Ethereum ASICs that exists today are only marginally better per watt than a commodity. GPUs and the way that ProgPOW has been designed. Yes of course somebody can always make a GPU as an ASIC but the amount of benefit I'll be able to get is vastly reduced. So even after a year if they spent millions of dollars designing and an ASIC might only be 10% faster maybe 20 percent more efficient. It's such a small difference that it won't be effectively the difference between one generation and the next of AMP GPU you are an NVIDIA GPU you it's not going to be the way that we've seen with other ASICS or with the Eth Hash ASICS where you can get a 2 x benefit 

Martin: [00:59:21] That's the case then. I thought two worth watching. But in the event that that is not the case then yes I would. I would probably prefer switching to something which anyone can. 

Alexey: [00:59:38] Mr Else You said that the ASICS is currently a marginally better like how marginally because it isn't doesn't this defeat the purpose of the switch stay a marginally better. 

Mr Else: [00:59:50] So an Ethhash ASIC can be about 2X better than the ones that are on the market right now. I've used DDR4 only a little bit better but not much better than a GPU. We Know that DDR6 based ethhash ASIC are coming soon and those will be about 2x better than any existing GPU. 

Alexey: [01:00:15] Okay so that's what you mean by marginally okay. 

Mr Else: [01:00:21] All right. Yeah. So ProgPOW takes that 2x down 1.1X 1.2X. 

Greg Colvin: [01:00:35] At worst we'll be in a slow motion arms race 

Mr Else: [01:00:44] Exactly And the GPU companies are also won't be sitting still. So the state of the art for what commodity consumer can buy off the shelf will be in slow motion arms race with what they the mining ASIC manufacturers are making. 

Alexey: [01:01:03] So I am not generally opposed to this change. My main point of what I would like to find out before we make a decision is that whether we underestimated the actual effort to be such a switch on it because we know that there is algorithm that we know we can do verification. But essentially what are the things we need to do. And is there any other catches that we haven't looked at. Like certain elements of the infrastructure or ecosystem like light clients or whatever the mining protocols or anything which we haven't even looked at. And then we kind of assume that it's going to be done very quickly but might be not. So do we have any blind spots. Should we look at any blind spots that we might have missed. 

Hudson: [01:01:59] Well it sounds like that's a good idea. go ahead Martin. 

Martin: [01:02:03] No I was going to say that that was one of the reasons to spin up the test not to see that we could get more clients and more we could do CPU mining we could do GPU mining. We can have fast synching I don't know if we have any light clients on it but it's lifetime verification is the same as normal verification OK. test net also has a crew that runs it. OK of course is who is using it. 

Alexey: [01:02:44] hey've already upgraded these things like what is the protocol that they call using. 

Martin: [01:02:50] No. Frank Gowen on the call. He works on a miner software Andrea Frankie 

Hudson: [01:03:04] Andrea I believe he is on here. She's on the air. Someone's on here. Are you on. 

Andrea: [01:03:12] Yes I'm here. Well and. Actually, I worked a lot to integrate ProgPOW into F miner. So the normal ethhash and ProgPOW can live together. Actually, they share the same dark memory area which is generated by the classic ethash kernel and things are going pretty well. Miner is working. The test net is working but actually it's a two-small test net. We have a few nodes the hashing power is very low. There are not particular problems I want just to add a few notes about the addition of ProgPOW what does it mean for miners. While it's pretty easy for AMD users to switch to the new algorithm it's a bit of a little bit trickier for NVIDEA users because the runtime compilation of the kernels requires that the video tool kit is installed on board. So, this mean a little more space needed on rigs which are driven by USB sticks or whatever and a little bit more of computing power. Just for the needs of the compiler to switch very rapidly on ProgPOW periods changes on Monday. 

Mr Else: [01:05:01] Oh I'll chat with you. Off line you don't actually need the full tool kit to do it to the compilation. 

Andrea: [01:05:11] Yeah. No I'm trying to reduce at the most the elements of the tool kit needed for the full the compilation but I will gladly chat with you. To to do to get the smaller size possible. Actually, all the implementations have a little hole that is in during the ProgPOW period switches all the miners stay silent for half a second. At least for the time needed to compile the kernel. I think we can easily implement and a synch of the pre-compilation of the kernel so so we can give continuity to all of the mining activity on the on the devices. And one last thing I think it might be related even if it's not directly related to the theorem itself. I think it's the adoption of the theory of stratum2.0 for. Communicating among miners and pools would help reduce significantly the bandwidth use it to signal all the works and might also if needed in the future integrate the revisions of the programmable protocol. So if it will ever happen that we start with that a revision of a ProgPOW which is actually the 0.9.2 to get to one 1.0. We can't easily implement the switches without changing the structure of the miner itself. That's my notes about the matter. 

Martin: [01:07:24] So did the demand we're talking about those silent half a second was that during that period or epoch change. 

Andrea: [01:07:33] During that period change. Epoch change actually cannot be prefixed unless you have a lot of very consistent space on the GPU which is actually possible for 6 gigabytes GPUs. But it's half a second in period changes. 

Martin: [01:07:59] So 50 blocks 

Andrea: [01:08:02] Yeah but as I said it's quite trivial to pre-compiled the kernel the new kernel while the old one are still running of the GPU you because at least for NVIDEA that the compilation that as far as I understand is completely Host process. It's not on the GPU. 

Alexey: [01:08:28] And so Andrea would you say that the is majority supporting this this new whole grid the. 

Andrea: [01:08:36] New Ethereum 2.0 strategy proposal yes does support it actually is not effective in use it even if I worked with Peter Pratcher would have implemented it in for their pool. And We have a couple of testing points which are working very well just yesterday with a collaborator of Peter We have tested that and ethereal stratum2.0 all in bundle with ProgPOW which is working quite fine OK. 

Alexey: [01:09:16] I mean so my question to basically everybody is that how much work do we have left for the core developers how much work do we have for the mining pools. Like if there is not much left and work to be done by core developers then I'm pretty happy to just sort of like wait till oh other people just finish their work and tell us when they're ready. Well of course they might need to have some certainty whether this change is going through but we can at least sort of gauge how much of our involvement is actually left in the process. What do you think? 

Andrea: [01:09:49] . Well you asked me? 

Alexey: [01:09:54] Not just you but everybody so my main question is that because this is the core of calls is it how much more time and effort or the core developers need to be spent on this change. And like you said minimal. Is it like medium is it large. Because I'm pretty happy if the rest of the work is proceeding somewhere else and then we can just make a decision on that basis. 

Andrea: [01:10:21] Well I'll go ahead. Sorry. I can't give you my personal opinion about that though the work on the mining side is pretty much done. What we are lacking now is a serious test actually the Gangnam network is mining a bunch of block of empty blocks. We have no transactions. I don't have a clear idea which is the impact of a slightly longer life of verification of the transactions. What is working now is a test method which is doing basically nothing. It's only producing a bunch of empty blocks. It works. The Stop that happened. It was only due to the fact that there was practically only a miner keeping the chain running. We have a very few very low hash rate at this very moment, there are less than 40 mega hashes. And my test rig alone is producing 36. So actually no one is participating actively in the testing of the network. There are no transactions. And I do not have a clear idea of what might be the impact for large pools to implement all the stock needed for power. I can tell on the F miner side that 95 percent of the work has been done. It's working and we need only to go through the optimization phase if there are any optimizations left to be done for the rest, the protocol is here. Peter is providing a very useful and valuable support to integrate ProgPOW into mining pools. Maybe an extensive test on a real crowded chain is needed before we take any decision about the schedule of the adoption. 

Martin: [01:13:05] Well I mean the only such test net we have is is Ropsten. So that would mean we would switch Ropsten to ProgPOW and then decide if we would go with ProgPOW which is a little bit about how we should do it. 

Karalabe: [01:13:22] Wow. One thing that we can do is to create a shadow fork of Ropsten, basically just launch a few nodes that switch over to ProgPOW and have the two chains coexist and everybody can still use the original Ropsten. The Original Ropsten will still have the exact same transactions but we'll just piggy back on that and try. 

Alexey: [01:13:45] You mean just to re play the transactions across chains 

Karalabe: [01:13:48] Yeah exactly. 

Alexey: [01:13:49] Okay. Well eventually that will diverge. But for some time for some time it will work. 

Karalabe: [01:13:54] So at worst it won't function properly forever, but still. I mean it would be so if the if our only goal is to test the how things perform on a used chain then I think it would be more or less useful. Maybe 10 percent of the transactions will fail. But who cares 

Hudson: [01:14:17] We're trying to decide. Today is more do we want to go forward with ProgPOW and not develop a timeline quite yet. But I do understand Alexey that your concern is the amount of effort involved across teams and that amount of effort is going to be longer than the effects of you know putting it in in the first place or what it's trying to prevent. 

[01:14:44] No I just want to understand what is the. So if we have a system that work has already been done from the core developer said like how much more do we need to do. Or not. 

Pawel: [01:15:02] I can try answering this. So Firstly I would suggest to those that I tried to answer like what what's for the client. The developers want this to work left so I would suggest to do small change to our PC end point. I think it's called get work to also include mining algorithm. It's rather trivial we simply added block number to the response. And so because this is kind of the connection between mining pools and so on I'm not sure like every mining policy I think that maybe they have modified plans but in a way this is kind of the connection and the second and the second bigger part would be considering block verification. So what clients need to implement ProgPOW block Proof of work verification 

Alexey: [01:16:10] It is isn't it already implemented a couple of clients? 

Pawel: [01:16:13] Yes, we have. We have 3 implementations right. Its C++ Ropsten and Go, so this can be exposed of the library and whatever but if you want like pure Python and something like that it's not done. And so, this is all too good considering the other something we want to have or like it's optional. And I also I also propose to add other language bindings to my library. A promise to this sharp some time ago. It's not going very well because there's some problems with figuring out how to do it exactly what it's doable if that's acceptable solution. So, can I expose python and maybe javascript something like that maybe javascript will be more problematic because it might be useful to have javascript only implementation to be to be running in browsers. But I'm not sure if we have ethhash implementation of that anyway. So but I think that's the biggest and like something this we can considering not to be mandatory. To have for for every implementation we are currently considering as a on client. 

Alexey: [01:17:54] So what you're saying is that there's some work left for the kind of non major clients to do in terms of their work. 

Pawel: [01:17:59] Yes. Yes. And like at least we should like having that into consideration right to either support their teams on like figure out approach to it these like probably all the teams shoes should somehow response to that and say what do they need what they think should be day for implementing blog verification and then we can suggest some solutions or corporate work on work on some common solutions to that. There's multiple approaches to it but it's I think at this point it's some kind of open question. So maybe that's well we could collect some answers during next two weeks. 

Hudson: [01:18:59] Yeah and we can make. Well I mean I guess for the non-major clients to code it between now and the time that we would potentially launch it which would be. what is theoretically the soonest that we would want to do this. Has anyone kind of thought about that. Martin I thought you might have been throwing around numbers but that might've been someone else for like three or five months. 

Martin: [01:19:36] Yeah, I don't know if I threw around the numbers but I would. Prefer it to be I don't know. In this order or maybe late this quarter or next quarter. 

Hudson: [01:19:51] OK. That sounds like two to three months. Well really three to four at most. If it's this quarter. So let's. Actually, I have a question for Dimitri from the harmony team have you all looked at integrating ProgPOW and or can you estimate or give us an idea of the amount of work to be done. Because that would also help us understand where pantheon might be at. I mean I can also ask the Pantheon team as well. 

Dmitrii (Harmony): [01:20:21] I'm not sure about that I think because some take like two three weeks. 

Hudson: [01:20:28] OK pantheon what about you all do you have any idea. 

Meredith: [01:20:36] We haven't started implementing ProgPOW really looked at it a whole lot. I've looked over it briefly. It doesn't seem like a massive amount of work. But again, we haven't invested much time on it yet. 

Hudson: [01:20:50] OK thank you. I guess I couldn't talk to the other one sir. The other clients too. Nimbus. Have you all looked at this. Oh, I think you're still muted. Sorry. Is it better now. Yep. It's on now. 

Jacek: [01:21:12] All right. No, we haven't really looked at this we're not that's fine. No problem. 

Meredith: [01:21:19] And just a quick question Are there any test suites that we would be able to run against as we implement. 

Martin: [01:21:26] Yes. So there are. Yeah. There are test cases for everything from smaller functions math and the random so up to full blocks. Oh, yes course not to full. 

Danno Ferrin: [01:21:43] These test leads include the epoch transitions that we saw issues with. 

Martin: [01:21:45] With that you can do a minor yes so there are tests that that block one block. Twenty-nine thousand nine ninety nine and look thirty thousand. Thirty thousand one block fifty-nine thousand etc. So, you get the epoch transitions as well. 

Dimitriy Khoklov: [01:22:09] There are also difficulties this designed specifically for difficulty formula check. So basically, just file describing what was a previous block number what does the next block number. So, I think we could extend that tests to also check something. 

Martin: [01:22:30] The formula for calculating what difficulties required from a block doesn't change. 

Dimitriy Khoklov: [01:22:36] Yeah. So, I think we could extend those tests to check also as a proof of work some call I mean you mean in the same format he could generate a lot of cases for proof of work if you really need a. 

Hudson: [01:22:57] OK. So Alexey does that help a little bit. 

Alexey: [01:23:00] Yeah. And I have a suggestion. I think so. It looks to me that we want to hear back from the non-major client but at the same time we kind of we don't want to procrastinate too much and just leave the decision hanging in the air. So I would say that we might just do the. We might decide. What kind of conditional decision kind of thing that might decide to do to go ahead unless we you know there there's like some major problem found with another major client or something like that. I don't know because it seems to me that there is no big reason why not. Why don't we just go ahead and give people some certainty about. Why they. Because I guess the the mining pools and other people will just need to just go ahead to start working on their stuff right. 

Hudson: [01:23:53] Yeah, I think it would be good if we didn't procrastinate any more. I think you have it right. You hit the nail right on the head as there are other technical questions about ProgPOW that we can ask myself or Mr. Else while they're on here. 

Jacek: [01:24:09] I have one concern or one thing that we've learned from ETh hash which is that the verification time for ETh hash on mobile devices is too long. So that sort of causes us to have to resort to other solutions less satisfactory. This is one thing that I be looking at is is like when evaluating protocol later would be whether we can actually verify Blocks on devices which are not as powerful as computer right. So calculating the normal hashes is fine but calculating an easy hash of the block really takes too much time to however useful. 

Mr Else: [01:25:00] So ProgPOW is very much based on ethhash. It adds a little bit more math and the main loop and doubles the amount of memory that's consumed from the DAG. So if Eth Hash is to slow ProgPOW will also definitely be to slow. 

Karalabe: [01:25:26] I think last time I saw benchmarks contained no verification. I think the best numbers were that ProgPOW is about twice as slow. So nothing too insane but not pleasant either. 

Mr Else: [01:25:41] I saw what some that I thought were about one point five X depending on some variables and compilation. But yes, then in the range of one point five to two X. 

Alexey: [01:25:52] And Jacek what is that what are the other techniques you need to use to kind of go around the problem. There's this technique going to work this technique work. Would they work on a ProgPOW or not. 

Jacek: [01:26:05] Basically it means going over two different trust models. you know ultralight clients with some sort of staking or what. Like VIP Node those kinds of solutions which are like on a powerful device like an iPhone you get away with it. But on say emerging markets typical devices not at all. 

Alexey: [01:26:33] And then you what you need to verify essentially you verify that hash changed from the beginning read from the right. 

Jacek: [01:26:41] Let's say something like a light scene correct. You need to verify. Even to just keep upward with with blocks it becomes. 

Alexey: [01:26:50] Just keep verifying the blocks OK. 

Martin: [01:26:52] But Jacek in your in your model do what would you like to verify each and every block. or can you do opportunistic. A block replication once in a while. 

Jacek: [01:27:04] You could consider opportunistic verification. We haven't really done that far into it. And the one thing I know is that verifying every block was simply too slow too heavy and too draining on the battery and a bunch of other things I guess you could explore models where you verify blocks when you are about to create transactions. The point is more that. Sufficiently computationally intense compared to say. Sha sharp verification and that. That it prevents normal operations so to speak the kind of operation that you're seeing. And if Eth hash abstract. Well obviously we have to look at these alternative models. 

Alexey: [01:27:56] This is actually quite interesting because the since we are changing the Proof of work algorithm it's not only like. The burden but it's also an opportunity because if there isn't a solution to that which we can incorporate so we basically will not simply make it slower but we might actually solve this problem somehow. It's a kind of crazy thought. But for example can we. Like sort of do the double prove of work like that you can ProgPOW plus Shard three or in both of them have to be valid and then the light clients can simply check one of them. Does it work.? 

Jacek: [01:28:34] And that's actually an idea that I thought about exploring but I haven't really looked at the logic of how that fit together. But basically, if you could include an extra hash that allows works kind of like a signature or something then. 

Alexey: [01:28:48] Well what I'm thinking about is that you basically need to provide two proofs of work. One is the based on ProgPOW and another one based on let's say Shard two or three whatever and which is much slower lower difficulty but still it will be it will be kind of hard to produce not as hard as the both prove of works but still hard. 

Mr Else: [01:29:10] So ethhash actually has that build in today and ProgPOW retains that where. The way these eth hash works is there is a cak ax of the header and the nonce. Then the E hash runs or ProgPOW runs and then there is a cak ax up the result. So a light client could just take the cak ax and verify those some clients use those for denial of service checks that you can check the cak ax if that's wrong then you don't bother calculating that he's harsh. So a light client could decide to just check the cak ax and not the proof of work not interact with the DAG at all. It's not a good verification but it's better than nothing. 

Alexey: [01:30:06] Could it be it could be. Could it be somehow strengthened or like. 

Pawel: [01:30:14] Well it's secure. Secure hash function. So I don't think it's something trivial that you can replace the that with something else if you don't want to poor memory that's that. You can replay the other hash function but doesn't change the the scheme of it. 

Jacek: [01:30:37] That's an interesting observation. 

Hudson: [01:30:39] Thanks. Cool. So not to get too much in the weeds. It sounds like what we've come to is that we are going to tentatively go ahead with ProgPOW and by tentatively what we mean is we're going ahead with it unless there's a major problem found within the testing or things of that nature. Is anyone feeling like that's not the case or if there's different feelings? Okay great. Then we will be going forward with ProgPOW. 

Alexey: [01:31:18] And just one more comment, sorry Hudson. Yes. Yes. Just so I think we have to make it clear and the kind of documented that we are not going to include any anymore changes into the hard fork. Because otherwise it will increase the complexity quite a lot. 

Hudson: [01:31:34] Yes, I think that's a good move. Does anyone have any comments on that statement that we would not be including any more changes into a ProgPOW hard fork that would happen before the nine months and Istanbul hard fought. 

Afri: [01:31:49] No but I was saying that we should not go down down the rabbit hole. Whenever anyone comes up to try to squeeze it in. I would totally agree with Alexey here. 

Hudson: [01:32:01] Great. Do you have any other comments on this.? 

Afri: [01:32:06] Yeah maybe one small comment I would like. Yeah, I'm that guy again. Let's not rush it. I mean when we are ready that's. But I personally think two to three months is very ambitious especially if you have to consider that we need at least six weeks between or client releases and people keep having time to upgrade it. Then we maybe need to test it half of a sink to two months as possible and three months. Ambitious. 

Alexey: [01:32:39] I think now we can what we can do now is that we're not going to decide that the timeframe but we sort of decided we are going to go and then we request the comments from all the people that still need you to work on this about how long is this going to take. And then just based on that information we can decide because we do want everybody to be sufficiently prepared. Right. 

Afri: [01:33:02] Yeah. Makes sense. 

Hudson: [01:33:05] Yes, I think that's a logical next step. 

Martin: [01:33:08] But if we if we today have agreed that we're going with ProgPOW. With caveats then we yeah let's people do some homework until the next quarter call and see if and how they can implement this in their frameworks and maybe we can talk about timing in two weeks does that sound feasible. ? 

Hudson: [01:33:39] Yeah that sounds good. We can collect data between now and then. OK do we have any other comments. 

Greg Colvin: [01:33:49] This speaks to the general issue of. Whether we want to do this rigid corporate thing of Rigid scheduling. Or do the continuous integrations of when we get a decent set of features strictly to get out when we get them out. 

Hudson: [01:34:30] OK. Yeah I agree I think that's something we need to look at over time. Is a Ethmagicians Forum a good place to discuss that? Do you think or is there a better way. ? 

Greg Colvin: [01:34:40] No, It's a core dev issue. 

Hudson: [01:34:43] Oh I meant like the forum like the.... So just discuss it and the calls or do you have a suggestion on where where to do what I should say. 

Greg Colvin: [01:34:51] On the core dev channel . 

Hudson: [01:34:54] Oh yeah that makes sense. 

Greg Colvin: [01:34:56] To some extent here and now because the prog VFW is already a case of. Oh we have a nine month one but oh we're gonna break the rule for this important feature. 

Hudson: [01:35:09] I see we only have a few minutes so we can't do it today. But I agree there's something we need to come up with. 

Greg Colvin: [01:35:15] Put it On the agenda for the next meeting. 

Hudson: [01:35:18] OK. Sounds good to me. Thanks Greg. OK. So we only have a few minutes left and I want to make sure offer you got some time then. So, thank you Mrs If Mr. Ellis for attending and answering some of these questions and I look forward to further collaboration between you and the other corps dev teams as we try to implement this. OK. Let's see. Afri if you want to go back and just do a quick summary of kind of what you've been working on as far as HF coordination and what you were discussing earlier. 

Afri: [01:35:56] Yeah sure. So I was proposing to have fixed schedule for protocol upgrades and basically releasing all accepted proposals on a fixed schedule. And now I am requesting comments 

Hudson: [01:36:22] And should those comments Be in the Gitter channel. Is there an EIP that you have that like people can comment on.? Or what's the best avenue for that. 

Afri: [01:36:33] No there no EIP. But this would be a outcome of discussing this. I just want to have like I mean we are only like five minutes left. But I would just want to have any comments here from the core developers. This is excellent science or we want to go in the path because based on this decision I will continue my work on a very specific kind of specific specifying some documents like that. 

Martin: [01:37:01] Yeah, I'll go. I think it's great if we can get it hard for hard folks with the longer-term view what's the what's what kind of protocol the place want to do and when it's about time we actually start rolling with that model. I mean we discussed it in Mexico. It was quite a while ago. 

Hudson: [01:37:26] Oh yeah. Good times. Anybody else have comments. 

Danno Ferrin: [01:37:32] I support the general idea of a regularized hard forks and also, I think what I think is better than just regular hard works is the rigor we're putting into the milestones such as making sure our releases are six weeks before any hard for it would happen. Having a timeframe before that six weeks for minor clients and other people to come in and commit not commit you know just the milestones of what we need to make sure that we have our ducks in a row before we basically reboot the network. So those are the things that I find most exciting about a regular hard work and regular times. Give us a forcing function to make sure that we're doing these things at a particular time on a particular schedule. 

Lane: [01:38:14] You're just adding my voice of support as well. I support this I think in particular having a regular testing schedule and making sure we get ample testing in and no changes or landing you know kind of just before any sort of made it hard fork happens. I think it is a great idea and a great step towards more maturity project management. 

Hudson: [01:38:40] Any other comments. ? 

Karalabe: [01:38:46] So from my perspective at least from the Geth team doing regular releases scheduled releases worked out really nice. A lot better than trying to cram in features and then eventually do big major releases. So I think it's from a community perspective too it's much it's much better to be deterministic rather than having to wait half a year and wonder whether this shifting will arrive or not. So I'm all for regular releases. 

Hudson: [01:39:23] OK. Anybody else. ? 

Danno Ferrin: [01:39:28] Me again one thing we might want to add. In light of progPOW it is maybe some sort of consideration for earlier than scheduled forks such things as limiting the scope and the timeframe for those I think those would be valuable to add in some process. 

Karalabe: [01:39:46] Why ask. I don't think it's a it's an issue to have unique forks if need be or to rule out certain upgrades if need be. I think it's more about the general releasing of new features. 

Afri: [01:40:01] Yeah. So what happened as Constantinople took like one point five years. I don't have exact figures now but having like a strictly defined schedule for hot folks tries to achieve this goal to have these grades deployed regularity to remain that it does not oppose having hard forks like ProgPOW. It makes sense you know. 

Hudson: [01:40:40] Any other comments I think we're actually over time. So any last comment. All right. Thanks so much for putting that together offer me. Sounds like we're making good progress there and we're looking forward to what we talk about more in the next meeting. Thanks everybody for attending. Made some great progress today and I'll try to post the next agenda soon so we can add items to it and I'll be posting that in the core dev gitter chat again send me an email if you're interested in the Jan in person meeting in San Francisco and everybody have a great day or night. 
