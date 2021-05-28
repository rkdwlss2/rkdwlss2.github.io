---
layout: post
title: "Algospot Pi"
date: 2021-05-25 16:33:00 +0530
categories: C++
---

# algospot Pi

길이가 3일때, 4일때, 5일때를 구분해서 dp

classify함수를 통해서 점수 구현, 

string 생성자를 통해서 M.size()길이와 M[0]으로 초기화한걸로 1점일때 구현

```cpp
#include <iostream>
#include <string>
#include <cmath>
using namespace std;

const int INF = 987654321;
string N;

int classify(int a, int b) {
	string M = N.substr(a, b - a + 1);
	if (M == string(M.size(), M[0]))return 1;

	bool progressive = true;
	for (int i = 0; i < M.size() - 1; ++i) {
		if (M[i + 1] - M[i] != M[1] - M[0]) {
			progressive = false;
		}
	}
	if (progressive && abs(M[1] - M[0]) == 1) {
		return 2;
	}
	bool alternating = true;
	for (int i = 0; i < M.size(); i++) {
		if (M[i] != M[i % 2]) {
			alternating = false;
		}
	}
	if (alternating)return 4;
	if (progressive)return 5;
	return 10;
}

int cache[10002];

int memorize(int begin) {
	if (begin == N.size())return 0;
	int& ret = cache[begin];
	if (ret != -1)return ret;
	ret = INF;
	for (int L = 3; L <= 5; L++) {
		if (begin + L <= N.size()) {
			ret = min(ret, memorize(begin + L) + classify(begin, begin + L - 1));
		}
	}
	return ret;
}

int main() {
	ios::sync_with_stdio(0);
	cin.tie(0);
	int tc;
	cin >> tc;
	while (tc--) {
		cin >> N;
		fill(cache, cache + 10002, -1);
		cout<<memorize(0)<<'\n';
	}
}
```
