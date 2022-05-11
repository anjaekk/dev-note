계정 생성
```
CREATE USER username PASSWORD 'password';
```

특정 테이블에 대한 데이터 생성 및 수정 권한 추가
```
GRANT INSERT, UPDATE ON table_name TO username;
```

특정 테이블 읽기 권한
```
GRANT SELECT ON table_name TO username;
```

모든 테이블 읽기 권한
```
GRANT SELECT ON ALL TABLES IN SCHEMA schema_name TO username;
```

특정 시퀀스에 대한 모든 권한
```
GRANT ALL ON SEQUENCE 특정시퀀스명_id_seq TO username;
```
