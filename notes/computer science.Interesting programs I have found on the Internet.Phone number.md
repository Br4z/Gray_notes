---
id: ibbjakzpt8nt78mzn8aze61
title: Phone number
desc: ''
author: gcohara
source: https://exercism.org/tracks/cpp/exercises/phone-number/solutions/gcohara
updated: 1705266489923
created: 1705262123923
---

> The original code does not work on entries like `(NXX-NXX-XXXX-XXXX` or `NXX)-NXX-XXXXXX`, so I decided to just use regex to check if the entry is a valid number.

- Code.

	```CPP
	#include <regex>


	bool is_phone_number(std::string const &input){
		std::regex phone_number{ R"(^(\+)?(1)?\s*(([2-9]\d{2})|\(([2-9]\d{2})\))(\s*|-|\.)([2-9]\d{2})(\s*|-|\.)(\d{4})\s*$)" };
		std::smatch match{ };

		return std::regex_match(input, match, phone_number);
	}
	```

- Explanation.

	We can divide the regex expression into its functions.

	1. `^(\+)?(1)?`: optional international country code at the beginning.

	2. `((([2-9]\d{2})|(((([2-9]\d{2})|))`: optional area code in parentheses.

	3. `(\s*|-||)`: number separators.

	4. ``s*`: trailing space.
