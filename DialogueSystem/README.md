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
     Dialogue는 한명의 대사를 담게 되고 DialogueEvent클래스는 인물들을 담게된다.
     Dialogue의 contents는 그 인물의 각각의 대사를 담게된다. 
2. 실제 대화를 담게 될 스크립트
   * InteractionEvent
     ``` c#
     public class InteractionEvent : MonoBehaviour
      {
          [SerializeField]
          DialogueEvent dialogue;
      }
      ```
      이 스크립트를 오브젝트에 할당하면  다음과 같이 나오게 된다.
     ![image](https://github.com/iou-bohun/Unity_Study/assets/56661597/9dfb6fdc-5e48-4b64-bd9f-cdf1de9bcfaf)
3. 데이터르 넘겨주는 스크립트
   * DialogueParser
     ```c#
     public class DialogueParser : MonoBehaviour
      {
          public TextMeshProUGUI testtextl;
          public Dialogue[] parse(string _CSVFileName)
          {
              // 파싱할 데이터를 임시로 저장할 리스트 
              List<Dialogue> dialogueList = new List<Dialogue>(); //대사 리스트 생성 
              TextAsset scvData = Resources.Load<TextAsset>(_CSVFileName); //csv파일 저장
      
              string[] data = scvData.text.Split(new char[] { '\n' });//csv파일의 대사를 엔터를 기준으로(한 줄씩) 나눔
              
              //대사의 행 만큼 반복
              for(int i=1; i<data.Length;)// 1번째 행에는  안덱스가 들어가서 제외 ex) id, 이름, 대사
              {
                  testtextl.text = data[1];
      
                  if(++i < data.Length)
                  {
                      ;
                  }
              }
              return dialogueList.ToArray();//리스트를 반환 타입인 배열로 
          }
     
