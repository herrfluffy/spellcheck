spellcheck - a solution to Justin.tv's spellcheck problem:
http://www.twitch.tv/problems/spellcheck

Description and usage
=====================
	Two python scripts are provided: spellcheck and barrage. Both use /usr/share/dict/words as the hardcoded dictionary. To use a different dictionary, please change the 'dict' string variable in each script appropriately.
	
	spellcheck reads words from STDIN and prints the best spelling suggestion found per word or "NO SUGGESTION" if none can be found to STDOUT. If multiple spelling suggestions are valid, a random one is picked by Python's pseudorandom number generator.

	barrage takes a positive integer input as a commandline argument and chooses that many words from the dictionary via Python's pseudorandom number generator, mutates them, and prints the result to STDOUT. For example, `./barrage 3` would pick three words from the dictionary and return three mangled words to make output such as this:
	MMaLLLTT''s
	YuukkooTirrennnBBBirrgg'SSS
	SSSCCoRRRiiiDDD

	Piping the results of barrage into spellcheck provides automated spellchecking of random words in the dictionary. For example, if `./barrage 3 | ./spellcheck` was run with the mangled outputs in the example above, the results could look like this:
	>malt's
	>Yekaterinburg's
	>scurried

	'>' characters are printed as part of the program specification, and result output is not guaranteed to be identical every run since multiple spelling suggestions could be found by spellcheck.
