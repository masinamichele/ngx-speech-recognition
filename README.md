# NgxSpeechRecognition

## Demo

![demo](./speech.gif)

Run `ng serve` for a demo server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## See

[Support Browsers](https://caniuse.com/#feat=speech-recognition)

[Web Speech API -- MDN](https://developer.mozilla.org/ja/docs/Web/API/Web_Speech_API)

## API

### RxSpeechRecognitionService

```typescript
import { Component } from '@angular/core';
import { RxSpeechRecognitionService } from '@kamiazya/ngx-speech-recognition';

@Component({
  selector: 'demo-rx',
  templateUrl: './rx.component.html',
  styleUrls: ['./rx.component.css'],
  providers: [
    RxSpeechRecognitionService,
  ],
})
export class RxComponent {

  message = '';

  constructor(
    private service: RxSpeechRecognitionService,
  ) { }

  listen() {
    this.service
      .listen()
      .pipe(RxSpeechRecognitionService.resultList)
      .subscribe((list: SpeechRecognitionResultList) => {
        this.message = list.item(0).item(0).transcript;
        console.log('RxComponent:onresult', this.message, list);
      });
  }

}
```
