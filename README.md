## : : s p a c e 0 0 5

![space](https://github.com/nicolasbaez/space005/blob/master/space005.gif)

```processing
int div=8;
int ancho=512;
int alto=256;
int cantidad=(ancho/(ancho/div))*(alto/(alto/div));
int rojo[]=new int[cantidad];
int cuentaCuadros;
int k=0;
float zAngle;
float zz;
void setup() {
  size(512, 256, P3D);
  stroke(255);
  println(cantidad);
  for (int i=0; i<cantidad; i++) {
    rojo[i]=int(random(0, 256));
  }
}
void draw() {
  translate(width/2, height/2, -height);
  rotateX(radians(k*0.5));
  rotateY(radians(k*0.25));
  background(0);
  cuentaCuadros=0;
  for (float i=-width/2; i<width/2; i+=width/div) {
    for (float j=-height/2; j<height/2; j+=height/div) {
      fill(255, 0, 0, rojo[cuentaCuadros]);
      zAngle=map(cuentaCuadros, 0, cantidad, 0, 360*6);
      zz=map(sin(radians(zAngle+k)), -1, 1, -height/2, height/4);
      cuentaCuadros++;
     pushMatrix();
      translate(i, j, zz);
      rect(0, 0, width/div, height/div);
      popMatrix();
    }
  }
  k+=2;
  if (k<=360*4) {
    saveFrame("gif/space005-######.png");
    k++;
    println(k);
  }
}
```
