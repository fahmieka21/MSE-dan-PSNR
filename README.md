# Penghitung Nilai MSE , RMSE , dan PSNR

Aplikasi GUI Penghitung Nilai MSE , RMSE , dan PSNR
~~~
Nama  : Fachmi Eka Pangestu
NIM   : 311810084
Kelas : TI 18 D5
~~~

# 1. Tutorial Cara Membuat Applikasi GUI
ketik guide pada command windows lalu tekan enter

![image](https://user-images.githubusercontent.com/43899437/165760596-1e270d44-4020-4898-a4f8-8cea7cd5ce5f.png)

# 2. Creat New GUI
Pilih creat new GUI, tentukan lokasi penyimpanan lalu tekan OK

![image](https://user-images.githubusercontent.com/43899437/165761015-177ca967-de7e-4ffc-a579-2bb700ecd9f0.png)

# 3. Buat Tampilan GUI sesuai yang di inginkan
![image](https://user-images.githubusercontent.com/43899437/177663996-7fa25135-46cb-4780-b1f7-933a6501ef0c.png)

# 4. Buat Source Code
Untuk memanggil tombol fungsi pada source klik kanan pada tombol fungsi >> view callback >> callback
![image](https://user-images.githubusercontent.com/43899437/177664098-44f244ed-643d-4b34-91e7-816d02ecd316.png)

Membuat Source Code
~~~
function varargout = restorasi_citra_dengan_parameter(varargin)
% RESTORASI_CITRA_DENGAN_PARAMETER MATLAB code for restorasi_citra_dengan_parameter.fig
%      RESTORASI_CITRA_DENGAN_PARAMETER, by itself, creates a new RESTORASI_CITRA_DENGAN_PARAMETER or raises the existing
%      singleton*.
%
%      H = RESTORASI_CITRA_DENGAN_PARAMETER returns the handle to a new RESTORASI_CITRA_DENGAN_PARAMETER or the handle to
%      the existing singleton*.
%
%      RESTORASI_CITRA_DENGAN_PARAMETER('CALLBACK',hObject,eventData,handles,...) calls the local
%      function named CALLBACK in RESTORASI_CITRA_DENGAN_PARAMETER.M with the given input arguments.
%
%      RESTORASI_CITRA_DENGAN_PARAMETER('Property','Value',...) creates a new RESTORASI_CITRA_DENGAN_PARAMETER or raises the
%      existing singleton*.  Starting from the left, property value pairs are
%      applied to the GUI before restorasi_citra_dengan_parameter_OpeningFcn gets called.  An
%      unrecognized property name or invalid value makes property application
%      stop.  All inputs are passed to restorasi_citra_dengan_parameter_OpeningFcn via varargin.
%
%      *See GUI Options on GUIDE's Tools menu.  Choose "GUI allows only one
%      instance to run (singleton)".
%
% See also: GUIDE, GUIDATA, GUIHANDLES

% Edit the above text to modify the response to help restorasi_citra_dengan_parameter

% Last Modified by GUIDE v2.5 06-Jul-2022 19:06:10

% Begin initialization code - DO NOT EDIT
gui_Singleton = 1;
gui_State = struct('gui_Name',       mfilename, ...
                   'gui_Singleton',  gui_Singleton, ...
                   'gui_OpeningFcn', @restorasi_citra_dengan_parameter_OpeningFcn, ...
                   'gui_OutputFcn',  @restorasi_citra_dengan_parameter_OutputFcn, ...
                   'gui_LayoutFcn',  [] , ...
                   'gui_Callback',   []);
if nargin && ischar(varargin{1})
    gui_State.gui_Callback = str2func(varargin{1});
end

if nargout
    [varargout{1:nargout}] = gui_mainfcn(gui_State, varargin{:});
else
    gui_mainfcn(gui_State, varargin{:});
end
% End initialization code - DO NOT EDIT


% --- Executes just before restorasi_citra_dengan_parameter is made visible.
function restorasi_citra_dengan_parameter_OpeningFcn(hObject, eventdata, handles, varargin)
% This function has no output args, see OutputFcn.
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
% varargin   command line arguments to restorasi_citra_dengan_parameter (see VARARGIN)

% Choose default command line output for restorasi_citra_dengan_parameter
handles.output = hObject;

% Update handles structure
guidata(hObject, handles);

% UIWAIT makes restorasi_citra_dengan_parameter wait for user response (see UIRESUME)
% uiwait(handles.figure1);


% --- Outputs from this function are returned to the command line.
function varargout = restorasi_citra_dengan_parameter_OutputFcn(hObject, eventdata, handles) 
% varargout  cell array for returning output args (see VARARGOUT);
% hObject    handle to figure
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Get default command line output from handles structure
varargout{1} = handles.output;


% --- Executes on button press in pushbutton1.
function pushbutton1_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
try
    [filename,pathname] = uigetfile({'*.*'});
 
    if ~isequal(filename,0)
        axes(handles.axes1)
        cla reset
        set(gca,'XTick',[])
        set(gca,'YTick',[])
 
        axes(handles.axes2)
        cla reset
        set(gca,'XTick',[])
        set(gca,'YTick',[])
 
        axes(handles.axes3)
        cla reset
        set(gca,'XTick',[])
        set(gca,'YTick',[])
 
        set(handles.edit1,'String','')
        set(handles.edit2,'String','')
        set(handles.edit3,'String','')
        set(handles.edit4,'String','')
        set(handles.edit5,'String','')
        set(handles.edit6,'String','')
 
        Img = imread(fullfile(pathname,filename));
        [~,~,dim] = size(Img);
        if dim == 3
            Img = rgb2gray(Img);
        end
 
        axes(handles.axes1)
        imshow(Img)
        title('Citra Grayscale Asli')
        handles.Img = Img;
        guidata(hObject, handles)
    else
        return
    end
catch
end


% --- Executes on selection change in popupmenu1.
function popupmenu1_Callback(hObject, eventdata, handles)
% hObject    handle to popupmenu1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: contents = cellstr(get(hObject,'String')) returns popupmenu1 contents as cell array
%        contents{get(hObject,'Value')} returns selected item from popupmenu1


% --- Executes during object creation, after setting all properties.
function popupmenu1_CreateFcn(hObject, eventdata, handles)
% hObject    handle to popupmenu1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: popupmenu controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on selection change in popupmenu2.
function popupmenu2_Callback(hObject, eventdata, handles)
% hObject    handle to popupmenu2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: contents = cellstr(get(hObject,'String')) returns popupmenu2 contents as cell array
%        contents{get(hObject,'Value')} returns selected item from popupmenu2


% --- Executes during object creation, after setting all properties.
function popupmenu2_CreateFcn(hObject, eventdata, handles)
% hObject    handle to popupmenu2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: popupmenu controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end


% --- Executes on button press in pushbutton2.
function pushbutton2_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)
try
    Img = handles.Img;
    [row,col,~] = size(Img);
 
    val1 = get(handles.popupmenu1,'Value');
 
    switch val1
        case 1
            Img_noise = imnoise(Img,'salt & pepper',0.2);
        case 2
            Img_noise = uint8(double(Img)+60*rand(row,col));
        case 3
            Img_noise = uint8(double(Img)+10*randn(row,col));
        case 4
            Img_noise = uint8(double(Img)+raylrnd(20,row,col));
    end
 
    axes(handles.axes2)
    imshow(Img_noise)
    title('Citra Terkontaminasi Noise')
 
    MSE = sum(sum((Img-Img_noise).^2))/(row*col);
    RMSE = sqrt(MSE);
    PSNR = 10*log10(256*256/MSE);
 
    set(handles.edit1,'String',MSE)
    set(handles.edit2,'String',RMSE)
    set(handles.edit3,'String',PSNR)
 
    val2 = get(handles.popupmenu2,'Value');
 
    switch val2
        case 1
            Img_filter = imfilter(Img_noise,ones(3)/9);
        case 2
            Img_filter = imfilter(Img_noise,ones(5)/25);
        case 3
            Img_filter = medfilt2(Img_noise,[3 3]);
        case 4
            Img_filter = medfilt2(Img_noise,[5 5]);
    end
 
    axes(handles.axes3)
    imshow(Img_filter)
    title('Citra Hasil Restorasi')
 
    MSE = sum(sum((Img-Img_filter).^2))/(row*col);
    RMSE = sqrt(MSE);
    PSNR = 10*log10(256*256/MSE);
 
    set(handles.edit4,'String',MSE)
    set(handles.edit5,'String',RMSE)
    set(handles.edit6,'String',PSNR)
catch
end


% --- Executes on button press in pushbutton2.
function pushbutton2_Callback(hObject, eventdata, handles)
% hObject    handle to pushbutton2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)



function edit1_Callback(hObject, eventdata, handles)
% hObject    handle to edit1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of edit1 as text
%        str2double(get(hObject,'String')) returns contents of edit1 as a double


% --- Executes during object creation, after setting all properties.
function edit1_CreateFcn(hObject, eventdata, handles)
% hObject    handle to edit1 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function edit2_Callback(hObject, eventdata, handles)
% hObject    handle to edit2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of edit2 as text
%        str2double(get(hObject,'String')) returns contents of edit2 as a double


% --- Executes during object creation, after setting all properties.
function edit2_CreateFcn(hObject, eventdata, handles)
% hObject    handle to edit2 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function edit3_Callback(hObject, eventdata, handles)
% hObject    handle to edit3 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of edit3 as text
%        str2double(get(hObject,'String')) returns contents of edit3 as a double


% --- Executes during object creation, after setting all properties.
function edit3_CreateFcn(hObject, eventdata, handles)
% hObject    handle to edit3 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function edit4_Callback(hObject, eventdata, handles)
% hObject    handle to edit4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of edit4 as text
%        str2double(get(hObject,'String')) returns contents of edit4 as a double


% --- Executes during object creation, after setting all properties.
function edit4_CreateFcn(hObject, eventdata, handles)
% hObject    handle to edit4 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function edit5_Callback(hObject, eventdata, handles)
% hObject    handle to edit5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of edit5 as text
%        str2double(get(hObject,'String')) returns contents of edit5 as a double


% --- Executes during object creation, after setting all properties.
function edit5_CreateFcn(hObject, eventdata, handles)
% hObject    handle to edit5 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end



function edit6_Callback(hObject, eventdata, handles)
% hObject    handle to edit6 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    structure with handles and user data (see GUIDATA)

% Hints: get(hObject,'String') returns contents of edit6 as text
%        str2double(get(hObject,'String')) returns contents of edit6 as a double


% --- Executes during object creation, after setting all properties.
function edit6_CreateFcn(hObject, eventdata, handles)
% hObject    handle to edit6 (see GCBO)
% eventdata  reserved - to be defined in a future version of MATLAB
% handles    empty - handles not created until after all CreateFcns called

% Hint: edit controls usually have a white background on Windows.
%       See ISPC and COMPUTER.
if ispc && isequal(get(hObject,'BackgroundColor'), get(0,'defaultUicontrolBackgroundColor'))
    set(hObject,'BackgroundColor','white');
end

~~~

![image](https://user-images.githubusercontent.com/43899437/177664303-78ccf9b0-edec-4cbe-8444-3bf8ead52d47.png)

# 5. Running Aplikasi GUI
![running](https://user-images.githubusercontent.com/43899437/177664421-24ea545e-d6ee-4463-808d-bf479c349b8a.png)

# 6. Input Gambar
![image](https://user-images.githubusercontent.com/43899437/177664873-564452db-019e-4cdf-93ec-23f91ff3e0e8.png)
![image](https://user-images.githubusercontent.com/43899437/177665068-0916b6ed-38bd-4169-b426-266d24cea856.png)

# 7. Proses
![image](https://user-images.githubusercontent.com/43899437/177665150-58859b06-adf1-4617-a5fd-64c477fd849c.png)

# 8. Mean 3x3
![image](https://user-images.githubusercontent.com/43899437/177665170-bf6df126-df21-43a2-951e-5b906640bf1d.png)

# 8. Mean 5x5
![image](https://user-images.githubusercontent.com/43899437/177665242-7e78bd5a-334c-4d56-94e6-2cd56f1c5c24.png)
