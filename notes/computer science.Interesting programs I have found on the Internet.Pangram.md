---
id: x75rgdnzup4xfzopeef4tuz
title: Pangram
desc: ''
author: akkanath-1863715
source: https://exercism.org/tracks/cpp/exercises/pangram/solutions/akkanath-1863715
updated: 1705262614341
created: 1702749655260
---

- Code.

	```CPP
	#include <iostream>


	bool is_pangram(std::string str) {
		int32_t f = 0;

		for (char &c : str)
			f |= 1 << ((c & ~32) ^ 64);

		return !(~f & ((1 << 27) - 2));
	}
	```

- Explanation.

	- `(c & ~32)`: ASCII code of the uppercase letter.

		The difference between a normal letter and its uppercase version is separated by 32 numbers, or the 6th binary digit.

		> With that statement we are subtracting 32 from the ASCII code of the character.

		```CPP
		char c = 'a' // 97 = 1100001

		(c & ~32) // 1100001 & 011111 = 1000001 = 65
		```

		> This operation only makes sense in letters.

	- `((c1 & ~32) ^ 64)`: subtract 64 from the uppercase letter code. That code is equivalent to `((c1 & ~32) & ~64)`.

		```CPP
		char c = 'a' // 97 = 1100001

		((c & ~32) ^ 64) // 1000001 ^ 1000000 = 1
		```

		> This is useful for starting to enumerate the letters from 1 to 26.

	- `1 << ((c & ~32) ^ 64)`: obtain the power associated with the capital letter.

		```CPP
		char c = 'a' // 97 = 1100001

		1 << ((c & ~32) ^ 64) // 1 << 2 = 2^1
		```

		> This is achieved by using the shift operator (`<<`).

	- `f |= 1 << ((c & ~32) ^ 64)`: register letter in number.

		> We are using the `f` var like a bitset.

	After applying this operation to every letter found in the string `str`.

	> In this point if the `str` is a pangram the `f` must be $134217726 = 111111111111111111111111110$.

	- `((1 << 27) - 2)`: is the number that must be `f` if `str` contains all letters.

		Based on this [[demonstration | math.Series.Demostrations#forall-n--in-mathbb-n--satisfied-that-sum_-i--0-n--2i---2-n---1----1]].

		$$
		\sum_{ i = 0 }^n { 2^i } = 2^{ n + 1 } - 1 \quad \sum_{ i = 1 }^n { 2^i } = 2^{ n + 1 } - 2 \\[10 pt]

		n = 26 \quad \sum_{ i = 1 }^{ 26 } { 2^i } = 2^{ 27 } - 2
		$$

	- `!(~f & ((1 << 27) - 2))`: `str` is a pangram only if that "and" operation ends in a number full of zeros.

		If at least one letter was not found, the result of the "and" operation will contain a "1". Resulting in `true` with the statement `~f & ((1 << 27) - 2)` and `false` with the negation.

		```CPP
		std::string str = "bcdefghijklmnopqrstuvwxyz"; // Without the "a" letter

		f; // 111111111111111111111111100
		~f; // 11

		~f & ((1 << 27) - 2) // 11 & 111111111111111111111111110 = 10

		!(~f & ((1 << 27) - 2)) // false
		```

> Fun fact: if you put the symbol `@` the resulting `f` will be exactly $2^27 - 1 = 111111111111111111111111111$, that's because that symbol is $65$ in ASCII code, which makes `1 << ((c & ~32) ^ 64)` equal to $2^0$.
