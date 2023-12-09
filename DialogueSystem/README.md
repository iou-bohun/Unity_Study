# Dialogue System (Using CSV)
  CSV파일을 이용한 대화 시스템 / ?CSV : (Comma Split Value), 콤마로 데이터 열을 나눈 파일

1. 틀을 만들자
   * Dialogue 클래스와 DialogueEvent
``` c#
     public class Dialogue
{
    [Tooltip("대사 치는 캐릭터 이름")]
    public string name;
    [Tooltip("대사 내용")]
    public string[] contexts;
}

public class DialogueEvent
{
    public string name; //이벤트의 이름

    public Vector2 line; // 대사 라인
    public Dialogue[] dialogues;
}
```
한다
