# factorization


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
