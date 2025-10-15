# 5.8 State로 사용자 입력 관리하기

React에서 useState를 이용해 사용자 입력을 관리하는 3단계 발전 과정을 살펴보자.
----

## ✅ 1단계: 각각의 입력값을 개별 상태로 관리
```javascript

import { useState } from "react";

const Register = () => {
  const [name, setName] = useState("");
  const [birth, setBirth] = useState("");
  const [country, setCountry] = useState("");
  const [bio, setBio] = useState("");

  const onChangeName = (e) => {
     setName(e.target.value);
  };

  const onChangeBirth = (e) => {
     setBirth(e.target.value);
  };

  const onChangeCountry = (e) => {
     setCountry(e.target.value);
  };

  const onChangeBio = (e) => {
     setBio(e.target.value);
  };


  return (
    <div>
      <div>
        <input value={name} onChange={onChangeName} placeholder={"이름"} />
      </div>
      <div>
        <input value={birth} onChange={onChangeBirth} type="date" />
      </div>
      <div>
        <select value={country} onChange={onChangeCountry}>
          <option></option>
          <option value="kr">한국</option>
          <option value="us">미국</option>
          <option value="uk">영국</option>
        </select>
      </div>

      <div>
        <textarea value={bio} onChange={onChangeBio} />
      </div>
    </div>
  );
};

export default Register;
```

> **특징:**
> 각 필드마다 `useState`를 따로 선언.
> 간단하지만 **입력 항목이 많아질수록 코드가 길어짐**.
----
# 5.9 State로 사용자 입력 관리하기2

## ✅ 2단계: 객체 형태로 상태 통합

```javascript

import { useState } from "react";

const Register = () => {
  const [input, setInput] = useState({
    name: "",
    birth: "",
    country: "",
    bio: "",
  });

  const onChangeName = (e) => {
    setInput({
      ...input,
      name: e.target.value,
    });
  };

  const onChangeBirth = (e) => {
    setInput({
      ...input,
      birth: e.target.value,
    });
  };

  const onChangeCountry = (e) => {
    setInput({
      ...input,
      country: e.target.value,
    });
  };

  const onChangeBio = (e) => {
    setInput({
      ...input,
      bio: e.target.value,
    });
  };

  return (
    <div>
      <div>
        <input value={name} onChange={onChangeName} placeholder={"이름"} />
      </div>
      <div>
        <input value={birth} onChange={onChangeBirth} type="date" />
      </div>
      <div>
        <select value={country} onChange={onChangeCountry}>
          <option></option>
          <option value="kr">한국</option>
          <option value="us">미국</option>
          <option value="uk">영국</option>
        </select>
      </div>

      <div>
        <textarea value={bio} onChange={onChangeBio} />
      </div>
    </div>
  );
};

export default Register;

```
> **특징:**
> 모든 입력값을 **하나의 객체(input)** 로 묶어 관리.
> 상태 구조가 깔끔해졌지만, **`onChange` 함수의 중복이 많음**.

----
## ✅ 3단계: 하나의 onChange로 모든 입력 관리

```javascript
import { useState } from "react";

const Register = () => {
  const [input, setInput] = useState({
    name: "",
    birth: "",
    country: "",
    bio: "",
  });

  const onChange = (e) => {
    setInput({
      ...input,
      [e.target.name]: e.target.value, // property의 key로 설정
    });
  };

  return (
    <div>
      <div>
        <input value={input.name} onChange={onChange} placeholder={"이름"} />
      </div>
      <div>
        <input value={input.birth} onChange={onChange} type="date" />
      </div>
      <div>
        <select value={input.country} onChange={onChange}>
          <option></option>
          <option value="kr">한국</option>
          <option value="us">미국</option>
          <option value="uk">영국</option>
        </select>
      </div>

      <div>
        <textarea value={input.bio} onChange={onChange} />
      </div>
    </div>
  );
};

export default Register;
```

> **변경 포인트:**
> - 각 input에 `name` 속성을 추가.
> - `onChange` 함수 하나로 모든 필드의 입력값 처리.
> - `[e.target.name]: e.target.value` → 동적 키 설정으로 반복 제거.

> **장점:**
> ✅ 코드 중복 감소
> ✅ 확장성 높음 (새로운 필드 추가 시 `input` 객체에만 key 추가하면 됨)
> ✅ 유지보수 용이
