# Arduino
Repositório criado para armazenar os scripts das atividades realizadas sobre Arduino do Curso Técnico de Redes de Computadores - Escola SENAI de Informática

##Script - Sensor de Temperatura

int interruptor = 13; //O botão_deslizante está conectado no pino 13
int leitor;

void setup() {
  Serial.begin(9600); //Inicia o monitor Serial
  pinMode(A0,INPUT); //Define o pino A0 como entrada

  pinMode(2,OUTPUT); //pino 2 definido como saida
  pinMode(3,OUTPUT); //pino 3 definido como saida
  pinMode(4,OUTPUT); //pino 4 definino como saida
  pinMode(interruptor,INPUT);//pino 13 defiido como entrada
}

void loop() {
 
  //Exibe no Monitor Serial a temperatura do Rack
  Serial.print("A temperatura do Rack esta em: "); 
  Serial.print(temperatura);
  Serial.print(char(176));
  Serial.println("C");
  delay(1000); //Aguarde 1 segundo
    
  leitor = digitalRead(interruptor);

    if(leitor == HIGH)
    {
        if(temperatura <= 25) 
        {   digitalWrite(2,HIGH);
            digitalWrite(3,LOW);
           digitalWrite(4,LOW);
        }
        else if(temperatura >25 && temperatura <=70)
        { digitalWrite(3,HIGH);
          digitalWrite(2,LOW);
          digitalWrite(4,LOW);
        }
        else if(temperatura >70)  
        {   digitalWrite(4,HIGH);
            digitalWrite(2,LOW);
            digitalWrite(3,LOW);
        }   
    }
    else
    {      digitalWrite(4,LOW);
           digitalWrite(2,LOW);
           digitalWrite(3,LOW);  
    }

}
