<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cursive on Windows (Mac style) Cheat Sheet</title>
    <style>
        body { font-family: Arial, sans-serif; color: #333; }
        .header, .footer { background-color: #333; color: white; padding: 10px; text-align: center; }
        .header img { width: 150px; }
        .table { width: 100%; border-collapse: collapse; margin-bottom: 20px; }
        .table th, .table td { border: 1px solid #ddd; padding: 8px; }
        .table th { background-color: #5881D8; color: white; }
        .table tr:nth-child(even) { background-color: #f4f7fc; }
        .table tr:hover { background-color: #ddd; }
        .footer { font-size: 12px; }
    </style>
</head>
<body>

<div class="header">
    <h2>Cursive on Windows (Mac style) Cheat Sheet</h2>
</div>

<table class="table">
    <thead>
        <tr>
            <th colspan="2">Editing</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Slurp backwards</td>
            <td>Ctrl+Alt+J</td>
        </tr>
        <tr>
            <td>Slurp forwards</td>
            <td>Ctrl+Shift+K</td>
        </tr>
        <tr>
            <td>Barf backwards</td>
            <td>Ctrl+Alt+K</td>
        </tr>
        <tr>
            <td>Barf forwards</td>
            <td>Ctrl+Shift+J</td>
        </tr>
        <tr>
            <td>Splice</td>
            <td>Alt+S</td>
        </tr>
        <tr>
            <td>Split</td>
            <td>Alt+Shift+S</td>
        </tr>
        <tr>
            <td>Raise</td>
            <td>Ctrl+Quote</td>
        </tr>
        <tr>
            <td>Join</td>
            <td>Ctrl+Shift+S</td>
        </tr>
        <tr>
            <th colspan="2">Kill</th>
        </tr>
        <tr>
            <td>Kill sexp</td>
            <td>Alt+Shift+K</td>
        </tr>
        <tr>
            <td>Copy as kill</td>
            <td>Alt+K</td>
        </tr>
        <tr>
            <td>Move form down</td>
            <td>Ctrl+Shift+Down</td>
        </tr>
        <tr>
            <td>Move form up</td>
            <td>Ctrl+Shift+Up</td>
        </tr>
    </tbody>
</table>

<table class="table">
    <thead>
        <tr>
            <th colspan="2">Writing</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Wrap with ""</td>
            <td>Ctrl+Shift+Quote</td>
        </tr>
        <tr>
            <td>Wrap with ()</td>
            <td>Ctrl+Shift+9</td>
        </tr>
        <tr>
            <td>Wrap with []</td>
            <td>Ctrl+Open Bracket</td>
        </tr>
        <tr>
            <td>Wrap with {}</td>
            <td>Ctrl+Shift+Open Bracket</td>
        </tr>
        <tr>
            <td>Close () and newline</td>
            <td>Ctrl+Shift+0</td>
        </tr>
        <tr>
            <td>Close [] and newline</td>
            <td>Ctrl+Close Bracket</td>
        </tr>
        <tr>
            <td>Close {} and newline</td>
            <td>Ctrl+Shift+Close Bracket</td>
        </tr>
    </tbody>
</table>

<table class="table">
    <thead>
        <tr>
            <th colspan="2">Testing</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Run tests in current NS in REPL</td>
            <td>Ctrl+Semicolon</td>
        </tr>
        <tr>
            <td>Run test under caret in REPL</td>
            <td>Ctrl+Shift+Semicolon</td>
        </tr>
        <tr>
            <td>Re-run last test action in REPL</td>
            <td>Alt+Shift+R</td>
        </tr>
        <tr>
            <td>Clear all test markers</td>
            <td>Ctrl+Shift+Backspace</td>
        </tr>
    </tbody>
</table>

<table class="table">
    <thead>
        <tr>
            <th colspan="2">REPL</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Execute REPL Current Statement</td>
            <td>Ctrl+Enter | Shift+Enter</td>
        </tr>
        <tr>
            <td>Load File in REPL</td>
            <td>Ctrl+Shift+L</td>
        </tr>
        <tr>
            <td>Sync files in REPL</td>
            <td>Ctrl+Shift+M</td>
        </tr>
        <tr>
            <td>Send top form to REPL</td>
            <td>Ctrl+Shift+P</td>
        </tr>
        <tr>
            <td>Send form before caret to REPL</td>
            <td>Ctrl+Alt+Shift+P</td>
        </tr>
        <tr>
            <td>Switch REPL NS to current file</td>
            <td>Alt+Shift+N</td>
        </tr>
        <tr>
            <td>Jump to REPL editor</td>
            <td>Ctrl+Alt+R</td>
        </tr>
        <tr>
            <td>Jump to REPL output pane</td>
            <td>Ctrl+Alt+O</td>
        </tr>
        <tr>
            <td>Search REPL history</td>
            <td>Ctrl+Alt+E</td>
        </tr>
        <tr>
            <td>Next REPL history item</td>
            <td>Ctrl+Down</td>
        </tr>
        <tr>
            <td>Previous REPL history item</td>
            <td>Ctrl+Up</td>
        </tr>
        <tr>
            <td>View macro expansion</td>
            <td>Ctrl+Alt+Shift+M</td>
        </tr>
        <tr>
            <td>Print last exception</td>
            <td>Ctrl+Alt+Shift+E</td>
        </tr>
    </tbody>
</table>

<table class="table">
    <thead>
        <tr>
            <th colspan="2">Refactoring</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Thread form</td>
            <td>Ctrl+Alt+Comma</td>
        </tr>
        <tr>
            <td>Unthread form</td>
            <td>Ctrl+Alt+Period</td>
        </tr>
        <tr>
            <td>Rename</td>
            <td>Shift+F6</td>
        </tr>
        <tr>
            <td>Extract Variable</td>
            <td>Ctrl+Alt+V</td>
        </tr>
        <tr>
            <td>Inline</td>
            <td>Ctrl+Alt+N</td>
        </tr>
    </tbody>
</table>

<table class="table">
    <thead>
        <tr>
            <th colspan="2">Other</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Select Around</td>
            <td>Ctrl+W</td>
        </tr>
        <tr>
            <td>Narrow Selection</td>
            <td>Ctrl+Shift+W</td>
        </tr>
        <tr>
            <td>Move Forward</td>
            <td>Ctrl+Left</td>
        </tr>
        <tr>
            <td>Move Backward</td>
            <td>Ctrl+Right</td>
        </tr>
        <tr>
            <td>Show Element Type</td>
            <td>Alt+=</td>
        </tr>
    </tbody>
</table>

<div class="footer">
    <p>Published 23rd January, 2017. Updated 25th January, 2017. Page 1 of 1.</p>
    <p>Cheatographer: J. Pablo Fernández (pupeno) via cheatography.com</p>
</div>

</body>
</html>
