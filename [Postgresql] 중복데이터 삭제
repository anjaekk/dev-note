DELETE FROM [테이블 명]
WHERE ctid IN ( 
	SELECT A.ctid FROM ( 
		SELECT ctid, ROW_NUMBER() over (
			PARTITION BY [id 제외 field명들]  ORDER BY id) AS num FROM [테이블 명]) A WHERE A.num > 1 )
