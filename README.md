# algoExpert algorithms question answers:

2- Validate Subsequence:
answer 1 => 

function isValidSubsequence(array, sequence) {
	let isExist = true;
  const indexedArray = array.filter(e => sequence.includes(e));
	const isSamedArray = array.every(e => sequence.every(i => e === i));
	if(!isSamedArray) {
			if(indexedArray.length === sequence.length) {
		for(let i=0; i<indexedArray.length; i++) {
			if(indexedArray[i] !== sequence[i]) {
				isExist = false;
			}
		}
	} else {
		isExist = false;
	}
	}

	return isExist;
}

answer 2 => 

function isValidSubsequence(array, sequence) {
	let isExist = true;
	let index = 0;
  const indexedObject = array.reduce((acc,curr) => {
		if(sequence.includes(curr)) {
			acc[index] = curr;
			index+=1;
		}
		return acc;
	}, {});
	const isSamedArray = array.every(e => sequence.every(i => e === i));
	if(!isSamedArray) {
	if(array.length >= sequence.length && sequence.length === Object.keys(indexedObject).length) {
			for(let i = 0; i<sequence.length;  i++) {
		if(indexedObject[i] !== sequence[i]) {
			isExist = false;
			break;
		}
	}
	} else {
		isExist = false;
	}
	}

	return isExist;
}
