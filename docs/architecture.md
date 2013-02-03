# 기술 구조

## Base

- node.js
    - expressjs
    - mocha
- mongodb

## Models

    room = {
        id: "2130af201",   //uid
        creator: "doortts"
        name: "코드리뷰1반",
        attendee: [ 'doortts', 'garlic2', ...] //방 참가자들
        messages: { // 아래 정의된 메시지 객체들이 들어간다.
            "1" : { ... }, // 메시지 id와 메시지객체, id를 timestamp로 하면 어떨까?
            "2" : { ... },
            ...
        }
    }

    user = {
        id: "doortts",
        timestamp: "~~~", // 가입일자
        rooms: [""2130af201","...."] //자신이 들어갈 수 있는 방의 목록
    }

    message = {
        id: "1",
        timestamp: "~~~",
        room: "2130af201", //메시지가 적힌 방 id
        writerId: "doortts",
        content: "어제는 눈이 내렸다",
        codeContains: false,  // 코드가 포함되었는지 여부
        file: { .. }, // 첨부내용이 파일일 경우 아래의 파일 모델
        parent: "1"   // 해당 방에서 어떤 글에 대한 연관글로 적었을 때
        subMessages: [ { ... }, {....}, ... ] //연관글로 적으면 자신이 하나의 메시지 이면서 동시에 subMessages로도 들어가게 된다.
    }

    file = {
        id: "1",
        timestamp: "~~~",
        room: "2130af201", //파일이 업로드된 방 id
        filename: "~~",
        size: "~~~",
        sha1: "~~~"
    }


