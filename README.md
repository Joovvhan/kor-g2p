# kor-g2p
Implementing my own graphene-to-phoneme algorithm for Korean language

[국립국어원 한국어 어문 규범 표준 발음법](http://kornorms.korean.go.kr/regltn/regltnView.do?regltn_code=0002&regltn_no=394#a387)

[표준발음 변환기](http://pronunciation.cs.pusan.ac.kr/pronunc.htm)

- [x] 제1항: 표준 발음법은 표준어의 실제 발음을 따르되, 국어의 전통성과 합리성을 고려하여 정함을 원칙으로 한다.

---

- [ ] 제2항: 표준어의 자음은 다음 19개로 한다. ㄱㄲㄴㄷㄸㄹㅁㅂㅃㅅㅆㅇㅈㅉㅊㅋㅌㅍㅎ

- [x] 제3항: 표준어의 모음은 다음 21개로 한다. ㅏㅐㅑㅒㅓㅔㅕㅖㅗㅘㅙㅚㅛㅜㅝㅞㅟㅠㅡㅢㅣ

##### 제2항, 제3항, 제8항에 의거하여 초성, 중성, 종성의 총 개수을 67(19 + 21 + 27)개에서 47(19 + 21 + 7)개로 줄일 수 있다.
##### 본 프로젝트의 최종 목표은 종성 기호의 수를 줄이므로써 발생 빈도 수가 적은 겹받침의 자연스러운 합성을 가능케 하는 것이다.

---

- [x] 제4항: ‘ㅏ ㅐ ㅓ ㅔ ㅗ ㅚ ㅜ ㅟ ㅡ ㅣ’는 단모음(單母音)으로 발음한다.

- [x] 제5항: ‘ㅑ ㅒ ㅕ ㅖ ㅘ ㅙ ㅛ ㅝ ㅞ ㅠ ㅢ’는 이중 모음으로 발음한다.

- [ ] 제6항: 모음의 장단을 구별하여 발음하되, 단어의 첫음절에서만 긴소리가 나타나는 것을 원칙으로 한다.

- [ ] 제7항: 긴소리를 가진 음절이라도, 다음과 같은 경우에는 짧게 발음한다.

- [x] 제8항: 받침소리로는 ‘ㄱ, ㄴ, ㄷ, ㄹ, ㅁ, ㅂ, ㅇ’의 7개 자음만 발음한다.

##### 7종성법에 의하여 받침소리 기호를 7개로 축약할 수 있다.

---

- [ ] 제9항: 받침 ‘ㄲ, ㅋ’, ‘ㅅ, ㅆ, ㅈ, ㅊ, ㅌ’, ‘ㅍ’은 어말 또는 자음 앞에서 각각 대표음 [ㄱ, ㄷ, ㅂ]으로 발음한다.

- [ ] 제10항: 겹받침 ‘ㄳ’, ‘ㄵ’, ‘ㄼ, ㄽ, ㄾ’, ‘ㅄ’은 어말 또는 자음 앞에서 각각 [ㄱ, ㄴ, ㄹ, ㅂ]으로 발음한다.

- [ ] 제11항: 겹받침 ‘ㄺ, ㄻ, ㄿ’은 어말 또는 자음 앞에서 각각 [ㄱ, ㅁ, ㅂ]으로 발음한다.

- [ ] 제12항: 받침 ‘ㅎ’의 발음은 다음과 같다.

- [ ] 제13항: 홑받침이나 쌍받침이 모음으로 시작된 조사나 어미, 접미사와 결합되는 경우에는, 제 음가대로 뒤 음절 첫소리로 옮겨 발음한다.

- [ ] 제14항: 겹받침이 모음으로 시작된 조사나 어미, 접미사와 결합되는 경우에는, 뒤엣것만을 뒤 음절 첫소리로 옮겨 발음한다.(이 경우, ‘ㅅ’은 된소리로 발음함.)

- [ ] 제15항: 받침 뒤에 모음 ‘ㅏ, ㅓ, ㅗ, ㅜ, ㅟ’ 들로 시작되는 실질 형태소가 연결되는 경우에는, 대표음으로 바꾸어서 뒤 음절 첫소리로 옮겨 발음한다.

- [ ] 제16항: 한글 자모의 이름은 그 받침소리를 연음하되, ‘ㄷ, ㅈ, ㅊ, ㅋ, ㅌ, ㅍ, ㅎ’의 경우에는 특별히 다음과 같이 발음한다.

- [ ] 제17항: 받침 ‘ㄷ, ㅌ(ㄾ)’이 조사나 접미사의 모음 ‘ㅣ’와 결합되는 경우에는, [ㅈ, ㅊ]으로 바꾸어서 뒤 음절 첫소리로 옮겨 발음한다.

- [ ] 제18항: 받침 ‘ㄱ(ㄲ, ㅋ, ㄳ, ㄺ), ㄷ(ㅅ, ㅆ, ㅈ, ㅊ, ㅌ, ㅎ), ㅂ(ㅍ, ㄼ, ㄿ, ㅄ)’은 ‘ㄴ, ㅁ’ 앞에서 [ㅇ, ㄴ, ㅁ]으로 발음한다.

- [ ] 제19항: 받침 ‘ㅁ, ㅇ’ 뒤에 연결되는 ‘ㄹ’은 [ㄴ]으로 발음한다.

- [ ] 제20항: ‘ㄴ’은 ‘ㄹ’의 앞이나 뒤에서 [ㄹ]로 발음한다.

- [ ] 제21항: 위에서 지적한 이외의 자음 동화는 인정하지 않는다.

- [ ] 제22항: 다음과 같은 용언의 어미는 [어]로 발음함을 원칙으로 하되, [여]로 발음함도 허용한다.

- [ ] 제23항: 받침 ‘ㄱ(ㄲ, ㅋ, ㄳ, ㄺ), ㄷ(ㅅ, ㅆ, ㅈ, ㅊ, ㅌ), ㅂ(ㅍ, ㄼ, ㄿ, ㅄ)’ 뒤에 연결되는 ‘ㄱ, ㄷ, ㅂ, ㅅ, ㅈ’은 된소리로 발음한다.

- [ ] 제24항: 어간 받침 ‘ㄴ(ㄵ), ㅁ(ㄻ)’ 뒤에 결합되는 어미의 첫소리 ‘ㄱ, ㄷ, ㅅ, ㅈ’은 된소리로 발음한다.

- [ ] 제25항: 어간 받침 ‘ㄼ, ㄾ’ 뒤에 결합되는 어미의 첫소리 ‘ㄱ, ㄷ, ㅅ, ㅈ’은 된소리로 발음한다.

- [ ] 제26항: 한자어에서, ‘ㄹ’ 받침 뒤에 연결되는 ‘ㄷ, ㅅ, ㅈ’은 된소리로 발음한다.

- [ ] 제27항: 관형사형 ‘-(으)ㄹ’ 뒤에 연결되는 ‘ㄱ, ㄷ, ㅂ, ㅅ, ㅈ’은 된소리로 발음한다.

- [ ] 제28항: 표기상으로는 사이시옷이 없더라도, 관형격 기능을 지니는 사이시옷이 있어야 할(휴지가 성립되는) 합성어의 경우에는, 뒤 단어의 첫소리 ‘ㄱ, ㄷ, ㅂ, ㅅ, ㅈ’을 된소리로 발음한다.

- [ ] 제29항: 합성어 및 파생어에서, 앞 단어나 접두사의 끝이 자음이고 뒤 단어나 접미사의 첫음절이 ‘이, 야, 여, 요, 유’인 경우에는, ‘ㄴ’ 음을 첨가하여 [니, 냐, 녀, 뇨, 뉴]로 발음한다.

- [ ] 제30항: 사이시옷이 붙은 단어는 다음과 같이 발음한다.
