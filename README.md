# factorization

I can generate smooths incredibly fast now, just wrote the code.. so yea.. this is not a bluff, the math is below.. but if I delete it and don't disclose my PoC you can probably avert the worst disaster for a little longer. You have a few days at most to do the right thing. I have lost everything, you went after my manager and one of my best friends.. I have nothing left to lose at this point. So you can decide to do the right thing, or whatever happens, happens, and I couldn't care less anymore

Fyi, I am open to discuss reponsible disclosure. But you got to make right with my former manager. If I don't hear from anyone in the coming few days, expect the PoC to go online as soon as its finished...

What I wrote below works.. its a pretty elegant way to generate smooths. Find a coefficient combination in mod p1,p2,p3,p4, solve a linear congruence to figure out how often N needs to be subtracted to reach 0. Then subtract that from the coefficient and keep subtracking the modulus to find smooths while being garanteed to have atleast p1,p2,p3,p4 as factors. I just have this nagging feeling, especially having figured this out now.. that people must have known when I published my earlier work, it was 99% in the right direction, I just missed this final connection for a long time.. I just don't get it, none of this makes sense. 

Fucking chaos in my head. Sometimes I get so focused on details, I cant see the big picture anymore. Anyway.. by looking at combinations of coefficients in i.e p1,p2,p3,p4 we can quickly figure out how many times we need to subtract N to get a value that is garantueed to be a multiple of p1,p2,p3,p4 .. and once we have that, where p1,p2,p3,p4 is our factor base or whatever.. we can hopefully find some smooth numbers. It sounds better on paper then what public variants of QS are doing.. and they just seem to look at the case only where N is subtracted just once, which seems restrictive. I need to go ahead and write the implementation now. Having these quadratic coefficients really allows for a much better understanding of this entire semi-prime structure. Most public research just look at the case where the coefficient is 0 (aka a square). Hmm. There is something bothering me, because all of this goes really deep into divisibility, I don't just want to work with squares.. I wonder if there is a way to do something useful when the coefficient is 1 instead.. or 2.. or any other value. But I suspect that will be another 2 years of research to figure that out.


Final edit before shit is about to hit the fan: I ran the numbers. It works. I can just look for coefficient solutions in mod p that have a 0 in their set of solutions. Then generate combinations of those to create smooth numbers and just apply gaussian elim over gf(2) to find a square as in quadratic sieve. Make right what you did to my manager and I am willing to talk about responsible disclosure. If not, this will be the first of many. I'm just getting started. These last 2 years, they were the "learning phase", now that I know the mathematical tools and ideas.. watch what is going to happen. Should not have fired my manager for complete made up bullshit reasons out of petty revenge. Injustice should see equal reaction, or else it becomes normalized, and this is my equal reaction and I can promise you all hell is about to break loose now. You have one week. This PoC will be trivial to write as I can just edit an existing quadratic sieve PoC and plug in my own number theoretical findings for generating smooth numbers...  one week to make this right or face the consequences. Good luck.

Edit: Bleh, my coin just dropped. You know how in quadratic sieve, the hard part is finding smooth numbers over a factor base.... actually... I just realized my work makes it a lot easier and it was right infront of me all the time. I don't know why I didn't make that connection until just now... god damnit. I.e if 148 is a coefficient solution, one of its divisors if 37. So the square of 148 also has 37 as a divisor. Hence by selecting quadratic coefficient solutions, if they contribute a 0 solution, that tells us something about the divisor... hence I am fairly sure that allows someone to quickly find smooth numbers (and we can also subtract 4n from coefficient solutions to apply the same idea to the lower square.. as long the coefficient solution is 0, it doesn't matter, because then its literally just contributing multiples of mod m). It makes sense in my head... fuck my life, I have to write a PoC and publish it asap, bet these assholes are already patching behind embargo, they must have known about this.
@Msft I know youre reading this. Go to hell. This is for my former manager. It doesnt matter if you raise the security requirements on rsa certs. Im going to drop this PoC and keep going. This is it, this solves finding smooth numbers. Omfg, insomnia, but I need to start writing the PoC asap, the fuck did i not see this for half a year, I must be fucking stupid. Just search for 0 coefficient solutions mod m.. how easy is that lol. Ps: If you rehire my former manager or give him a shitload of money (in the many millions range), I might reconsider dropping the PoC, but in lack thereof.. prepare to feel my wrath.

Edit: Changed my mind. Going to keep the new research to myself. Whoever hires me can have access. Tired of this fucking shit. Unemployed for nearly 1,5 years now.

Edit: While working on my next iteration of the algorithm, I did notice plenty of mistakes and unverified assumptions in my paper. What I described as "rebasing" in my paper, can be skipped I believe. And some of the "limits" I talk about, only hold true with a semiprime whose two factors are of roughly equal bit length (as is recommended for RSA key generation). The entire LLL portion is bad and the result of my at the time limited understanding of linear algebra. I hope to correct many of my  mistakes when I release my next iteration soon, which also swaps out LLL for gaussian elimination, as at its core, solving for quadratic coefficients is a linear problem, albeit a fairly complex one. Everything that was uploaded here was the result of only one year of work which I started with pre-highschool level math knowledge (I dropped out). Now 6 months later, and having had some more time to reason about it, I have a much better understanding of it.. but it's a massive undertaking to get it all in shape for release.. but hopefully this month (feb 2025). I am also still looking for a job after more then a year of unemployment: big_polar_bear1@proton.me
Life has been a shit show ever since summer of 2023 when I was harassed at the MSFT campus, threatened with a gun outside my apartment, fired due to having a mental breakdown from all the harassment, people and friends suddenly passing away,  my manager getting fired out of retaliation because he tried to stop MSFT from firing me.. being forced to leave the country, move half a world away from all the friends I had known for years.. I still don't know how to cope, I struggle with intense anger and depression, but I will break factorization, I don't care what it takes, I don't care if I end up living on the street, broke. I will succeed. Nobody believes in me, most people think I have lost my sanity, I don't care, I will succeed and I will punch my haters in their dumb faces if they ever cross my path.

update: New iteration swapping LLL for gaussian elimination coming soon....

This is a reupload of a deleted github repo.

Final notes and thoughts: by solving for squared quadratic coefficients we achieve an extremely low density. I have not yet enough experience with LLL to attack this using a proper bkz algo. I will continue my work, if you want access, pay me.

If you want to sponsor future research and have exclusive rights big_polar_bear1@proton.me
I also have windows 0days for sale, will accept crypto as payment. Do not care who buys, got to make a living since I cant get a job.

Note: The results from the paper assumes a semiprime with two factors of roughly similar bit length. As is relevant to RSA implementations. Minor tweaks need to be made otherwise.

Update 23 October: Uploaded the fixed version as factor2.sage. There is some info at the top of the file. Figure the rest out yourself. To improve of the results, you probably want to rewrite it to use a proper bkz reduction strategy. Additionally, if you can get it to run in a gpu and run more instances of LLL in paralell, that would greatly help. 
I have no intention of sharing anything else for free anymore. I may push some bug fixes in the future, but that is it. Thanks. If the script doesnt work and you cant find a bug, then read the math paper, and if you cant understand the math, not my problem.

Update 21 october: Looking to release newest iteration on friday. Reworked nearly everything, it now relies heavily on weight reduction. That seems to be the key to this.

Update 18 oct: Started trying to break a 150 bit key. Once I succeed, the revised version will be uploaded. Its running on a laptop in 12 parallel processes. If it works, it should prove my work. But either way, I am tired. My life is ruined and im very tired. 


Uodate 11 oct: Delaying release until next week, as I want to get it 100% right this time around. The current version on github is completely broken (but the paper is correct), there's a number of bugs in analyzing lll output. If it finds factors its random. I fixed all that in the upcoming release. Some things I fixed:

1. Sign issue breaking analyzeresult function completely
2. Reworked the strategy to put single smaller moduli in different columns. And then match it against small solutions
I.e if the y solution we want to find is 148, our lll matrix will find it by matching several columns against 3 mod 5.
(we only need to match against a very small modulus of the full y solution, this scales logarithmically, we do not need to bruteforce exponentially).
3. Reworking the weight reduction algorithm to delete partial results from the matrix completely as to reduce matrix dimensions.
4. Fixed numerous other bugs in LLL output parsing and also now calculating how many times the modulus needs to be added/subtracted.

Update 5 oct: sage script was buggy, reworked the strategy and fixed more bugs, revised version will get uploaded next week

See paper.pdf for info.

Backup: sandboxescaper.com
