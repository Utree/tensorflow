# 未来のデスクトップ -iOS APP-
## 使い方
1. Tensor Flow Liteのでもアプリをつくる
> [TensorFlow Lite](https://www.tensorflow.org/lite/demo_ios)のサイトを参考にして、でもアプリをつくる
```
$ git clone https://github.com/tensorflow/tensorflow
$ xcode-select --install
$ sudo gem install cocoapods
$ sh tensorflow/lite/examples/ios/download_models.sh
$ cd tensorflow/lite/examples/ios/camera
$ pod install
$ pod update
$ open tflite_camera_example.xcworkspace
```
2.  CameraExampleViewController.mmを編集
> ただし、"https://NGROK_URL/"はよしなに変更する

```
      if(labelCount == 0) {
          if([[label capitalizedString] isEqualToString:@"Pencil Box"]) {
              UIAlertController *alertController = [UIAlertController alertControllerWithTitle:@"ロックを解除しますか?"
                                                                                       message:@""
                                                                                preferredStyle:UIAlertControllerStyleAlert];
              
              [alertController addAction:[UIAlertAction actionWithTitle:@"はい"
                                                                  style:UIAlertActionStyleDefault
                                                                handler:^(UIAlertAction *action) {
                                                                    // 送信したいURLを作成し、Requestを作成します。
                                                                    NSURL *url = [NSURL URLWithString:@"https://NGROK_URL/unlock/"];
                                                                    NSURLRequest  *request = [[NSURLRequest alloc] initWithURL:url];
                                                                    // NSURLConnectionのインスタンスを作成したら、すぐに
                                                                    // 指定したURLへリクエストを送信し始めます。
                                                                    // delegate指定すると、サーバーからデータを受信したり、
                                                                    // エラーが発生したりするとメソッドが呼び出される。
                                                                    NSURLConnection *aConnection = [[NSURLConnection alloc] initWithRequest:request delegate:self];
                                                                    
                                                                    // 作成に失敗する場合には、リクエストが送信されないので
                                                                    // チェックする
                                                                    if (!aConnection) {
                                                                        NSLog(@"connection error.");
                                                                    }
                                                                }]];
              
              [alertController addAction:[UIAlertAction actionWithTitle:@"いいえ"
                                                                  style:UIAlertActionStyleDefault
                                                                handler:^(UIAlertAction *action) {
                                                                    // cancelボタンが押された時の処理
                                                                    
                                                                }]];
              
              [self presentViewController:alertController animated:YES completion:nil];
          } else if([[label capitalizedString] isEqualToString:@"Rubber Eraser"]) {
              UIAlertController *alertController = [UIAlertController alertControllerWithTitle:@"ロックしますか?"
                                                                                       message:@""
                                                                                preferredStyle:UIAlertControllerStyleAlert];
              
              [alertController addAction:[UIAlertAction actionWithTitle:@"はい"
                                                                  style:UIAlertActionStyleDefault
                                                                handler:^(UIAlertAction *action) {
                                                                    // 送信したいURLを作成し、Requestを作成します。
                                                                    NSURL *url = [NSURL URLWithString:@"https://NGROK_URL/lock/"];
                                                                    NSURLRequest  *request = [[NSURLRequest alloc] initWithURL:url];
                                                                    // NSURLConnectionのインスタンスを作成したら、すぐに
                                                                    // 指定したURLへリクエストを送信し始めます。
                                                                    // delegate指定すると、サーバーからデータを受信したり、
                                                                    // エラーが発生したりするとメソッドが呼び出される。
                                                                    NSURLConnection *aConnection = [[NSURLConnection alloc] initWithRequest:request delegate:self];
                                                                    
                                                                    // 作成に失敗する場合には、リクエストが送信されないので
                                                                    // チェックする
                                                                    if (!aConnection) {
                                                                        NSLog(@"connection error.");
                                                                    }
                                                                }]];
              
              [alertController addAction:[UIAlertAction actionWithTitle:@"いいえ"
                                                                  style:UIAlertActionStyleDefault
                                                                handler:^(UIAlertAction *action) {
                                                                    // cancelボタンが押された時の処理
                                                                    
                                                                }]];
              
              [self presentViewController:alertController animated:YES completion:nil];
          }
      }
```

3. TeamとBundle　Identifierを編集

4. 実行
## 参考サイト
- https://www.tensorflow.org/lite/demo_ios
- https://qiita.com/TakayukiNJ/items/8233cb91c187b1450816
- https://www.yoheim.net/blog.php?q=20120605
## License

[Apache License 2.0](LICENSE)
