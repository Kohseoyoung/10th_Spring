### 워크북 캡쳐


### 워크북 리뷰


### 미션
1. INSERT INTO review (member_id, store_id, score, content, created_at, updated_at)
VALUES (1, 101, 5.0, '음 너무 맛있어요 포인트도 얻고 맛있는 맛집도 알게 된 것 같아 너무나도 행복한 식사였답니다. 다음에 또 올게요!!', NOW(), NOW());

2. SELECT name, email, phone_number, point
FROM member
WHERE member_id = 1; 

3. SELECT m.reward_point, [s.name](http://s.name/)  AS store_name, m.conditional, mm.status, mm.created_at
FROM member_mission mm
JOIN mission m ON mm.mission_id = m.mission_id
JOIN store s ON m.store_id = s.store_id
WHERE mm.member_id = 1
AND mm.status IN ('CHALLENGING', 'COMPLETE')
ORDER BY mm.created_at DESC
LIMIT 10 OFFSET 0;

4. <유저 미션 현황>

SELECT

COUNT(CASE WHEN mm.is_complete = 1 THEN 1 END) AS complete_count,

COUNT(*) AS total_attempt_count

FROM member_mission mm

WHERE mm.member_id = 1;

---

<도전 가능한 미션 목록>

SELECT m.mission_id, m.store_id, m.point, m.conditional, m.deadline, m.created_at
FROM mission m
WHERE m.mission_id NOT IN (
SELECT mission_id
FROM member_mission
WHERE member_id = 1
)
ORDER BY m.created_at DESC
LIMIT 10 OFFSET 0;


