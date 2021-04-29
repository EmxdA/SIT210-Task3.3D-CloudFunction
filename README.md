# SIT210-Task3.3D-CloudFunction

# Using Pi to publish event
void setup() 
{
}
void loop()
{
		Particle.publish("Raspberry_pi", "wave");
		delay(10000);
		Particle.publish("Raspberry_pi", "pat");
		delay(5000);
}



# Argon subscribes to event
int boardLed = D5;
int boardLed1 = D7;

void setup() {
  pinMode(boardLed,OUTPUT); 
  pinMode(boardLed1,OUTPUT); 
  Particle.subscribe("Raspberry_pi", myHandler);
}


void loop() {
}

void myHandler(const char *event, const char *data)
{
    if (strcmp(data, "wave") == 0)
    {
        digitalWrite(boardLed,HIGH);
        delay(1000);
        digitalWrite(boardLed,LOW);
        delay(1000);
        digitalWrite(boardLed,HIGH);
        delay(1000);
        digitalWrite(boardLed,LOW);
        delay(1000);
        digitalWrite(boardLed,HIGH);
        delay(1000);
        digitalWrite(boardLed,LOW);
        delay(1000);
    }
    else if(strcmp(data, "pat") == 0)
    {
        digitalWrite(boardLed1,HIGH);
        delay(1000);
        digitalWrite(boardLed1,LOW);
        delay(1000);
    }
}

