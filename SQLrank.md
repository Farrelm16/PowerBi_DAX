SELECT * FROM (
SELECT *,row_number() OVER (PARTITION by concat(paperstack_id,manuscript_id) ORDER BY extracted_date desc) AS rnk
FROM submission.paperstack_author_activity paa
) tab
WHERE rnk=1;
