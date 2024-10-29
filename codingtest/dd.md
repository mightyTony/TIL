# 1. String 

# .length() : 문자열의 길이를 반환
# .equals(a) : 문자열이 a와 같은지 비교
# .charAt(index) : 특정 위치(index)의 문자 반환
# .substring(start, end) : 문자열의 일부(start에서 end 전까지) 반환
# .concat(a) : 문자열과 a를 연결
# .toUpperCase() : 문자열을 대문자로 변환
# .toLowerCase() : 문자열을 소문자로 변환
# .trim() : 문자열의 앞뒤 공백 제거
# .contains(a) : 문자열에 a가 포함되었는지 확인
# .split(a) : 문자열을 a를 기준으로 분리하여 배열로 반환
# .replace(old, new) : 문자열 내의 old를 new로 치환
# .startsWith(a) : 문자열이 a로 시작하는지 확인
# .endsWith(a) : 문자열이 a로 끝나는지 확인
# .indexOf(a) : 문자열 내에서 a가 처음으로 나타나는 위치 반환
# .toCharArray() : 문자열을 문자 배열로 변환
# String.format() : 형식화된 문자열 반환


# 1-1 Stringbuilder, Stringbuffer
StringBuilder sb = new StringBuilder("");
StringBuffer sb = new StringBuffer();
# .append(a) : 문자열 또는 데이터를 끝에 추가
# .insert(index, a) : 지정한 위치에 문자열 또는 데이터를 삽입
# .delete(start, end) : 지정한 범위의 문자열을 삭제 (start에서 end 전까지)
# .deleteCharAt(index) : 지정한 위치의 문자를 삭제
# .replace(start, end, str) : 지정한 범위를 새로운 문자열로 대체
# .setCharAt(index, ch) : 특정 위치의 문자를 다른 문자로 변경
# .reverse() : 문자열을 뒤집음
# .length() : 현재 문자열의 길이를 반환
# .substring(start, end) : 지정된 범위의 부분 문자열을 반환
# .charAt(index) : 특정 위치의 문자를 반환
# .toString() : StringBuilder 또는 StringBuffer 객체를 String으로 변환하여 반환
# .capacity() : 현재 객체의 용량을 반환
# .setLength(newLength) : 문자열의 길이를 지정된 값으로 설정 (길이를 줄이면 그 이후 문자는 삭제)
---

# 2. Math

.abs(): 절대값
.random() : 0.0~1.0 double 난수 
.max(a,b) : a,b 중 큰 것 
.min(a,b) : a,b 중 작은 것
.round( a ) : 소수점 a 자리 반올림 
.pow(a,b) : a^b
.sqrt(a) : a^2

---

# 3. ArrayList
List<E> list = new ArrayList<>();

.get(x)
.set(x)
.add(x)
.size()
.isEmpty()
.contains(x)
.indexOf(x) 
.clear()
.addAll()
.removeAll()

--- 
# 4. Arrays

Arrays.stream(배열).filter(value -> value.조건).toArray();
Arrays.sort(배열) : 오름차순 배열을 정렬함 