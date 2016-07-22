# manipulationADB
kết nối , kiểm tra ,logcat thiết bị android qua mạng wifi

### sử lý bằng C sharp

```
// hàm run commands line 
static void runCommand() {
    //* Create your Process
    Process process = new Process();
    process.StartInfo.FileName = "cmd.exe";
    process.StartInfo.Arguments = "/c DIR";
    process.StartInfo.UseShellExecute = false;
    process.StartInfo.RedirectStandardOutput = true;
    process.StartInfo.RedirectStandardError = true;
    //* lấy kết quả đầu ra khi thực hiện lệnh 
    process.OutputDataReceived += new DataReceivedEventHandler(OutputHandler);
    process.ErrorDataReceived += new DataReceivedEventHandler(OutputHandler);
    //* bắt đầu thực hiện tiến trình
    process.Start();
    process.BeginOutputReadLine();
    process.BeginErrorReadLine();
    process.WaitForExit();
}
static void OutputHandler(object sendingProcess, DataReceivedEventArgs outLine) {
    //* Do your stuff with the output (write to console/log/StringBuilder)
    Console.WriteLine(outLine.Data);
}
```
### demo 2 
```
ProcessStartInfo info = new ProcessStartInfo(); 
info.Arguments = "/C ping 127.0.0.1"; 
info.WindowStyle = ProcessWindowStyle.Hidden; 
info.CreateNoWindow = true; 
info.FileName = "cmd.exe"; 
info.UseShellExecute = false; 
info.RedirectStandardOutput = true; 
using (Process process = Process.Start(info)) 
{ 
    using (StreamReader reader = process.StandardOutput) 
    { 
        string result = reader.ReadToEnd(); 
        textBox1.Text += result; 
    } 
} 
```
> ảnh minh họa hàm </br>
![gggqq](https://cloud.githubusercontent.com/assets/18228937/17046262/72ad93b4-4ffb-11e6-8b30-e230b762dc69.jpg)



