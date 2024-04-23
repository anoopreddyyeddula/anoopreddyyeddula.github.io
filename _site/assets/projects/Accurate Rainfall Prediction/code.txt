TESTING THE MODULE:
clc; clear all; close all;

% READ THE RAINFALL DATSET

[ndata, text, alldata] = xlsread('"/Users/Mounika Reddy/Desktop\RAINFALL CHENNAI.csv"','data');

ndataX=ndata(1:6000); chennai_rainfall=ndata(:,4); chennai_rainfall=chennai_rainfall(1:1000);

chennai_humidity=ndata(:,5); chennai_humidity=chennai_humidity(1:1000);

chennai_temp=ndata(:,6); chennai_temp=chennai_temp(1:1000);


xa=chennai_rainfall(1:1000); [r c]=size(xa); xa=reshape(xa,[c r]);
% **********************************************x***************************
% FETCH FUTURE DATA
%***************************************************************************    [f p]=uigetfile('*.xlsx');
 
[ndata2, text2, alldata2] = xlsread([p f],'data');

% *************************************************************************
% Change Here to give the Existing Dataset
% [ndata2, text2, alldata2] = xlsread('chennai.xlsx','data');
% ************************************************************************* fu_rainfall=ndata2(:,4);
MxFall=max(fu_rainfall); MnFall=min(fu_rainfall); AvgFall=mean(fu_rainfall);

figure, hist(MxFall);
title('Maximum Rainfall of the Month','FontSize',10);

totalcrf=numel(fu_rainfall) for kk=1:totalcrf
if (MxFall==fu_rainfall(kk)) stamp=kk;
end end

training_known_data=ndata2(:,4);

yda=training_known_data(1:1000); yea=chennai_rainfall(1:1000); ya=[yda yda];
inpp=xa;
 
xa=[xa xa];
[r1 c1]=size(ya); ya=reshape(ya,[c1 r1]);

[accuracy1]=SvmAlgorithm(xa,ya); targg=yda'; [fn1,fp1,tp1,tn1]=FFANN(inpp,targg);
accuracy2 = num2str(((tp1+tn1)/(tp1+tn1+fp1+fn1))*100) Precision = num2str((tp1/(tp1+fp1))*100)
Recall	= num2str((tp1/(tp1+fn1))*100)



[accuracy1 accuracy2]

msgbox([{'Accuracy='	accuracy2}  {'Precision='	Precision} {'Recall=' Recall}]);

maxmonth=max(training_known_data); for i=1:numel(training_known_data)
if training_known_data(i)==maxmonth stamp=i;
end end
alldata_month=training_known_data; month=alldata(:,4); showmonth=cell2mat(month(stamp))
 

[mname2]=monthlyPred(showmonth); msgbox([mname2,{'RF=' num2str(maxmonth) 'in cm'}]);

TRAINING THE MODEL:


clc; clear all; close all;

% READ THE RAINFALL DATSET
[ndata, text, alldata] = xlsread('chennai.xlsx','data');

ndataX=ndata(1:6000); chennai_rainfall=ndata(:,4); chennai_rainfall=chennai_rainfall(1:1000);

chennai_humidity=ndata(:,5); chennai_humidity=chennai_humidity(1:1000);

chennai_temp=ndata(:,6); chennai_temp=chennai_temp(1:1000);


xa=chennai_rainfall(1:1000); [r c]=size(xa); xa=reshape(xa,[c r]);
% **********************************************x***************************
% FETCH FUTURE DATA
%***************************************************************************
 
[f p]=uigetfile('*.xlsx');
[ndata2, text2, alldata2] = xlsread([p f],'data');

% *************************************************************************
% Change Here to give the Existing Dataset
% [ndata2, text2, alldata2] = xlsread('chennai.xlsx','data');
% ************************************************************************* fu_rainfall=ndata2(:,4);
MxFall=max(fu_rainfall); MnFall=min(fu_rainfall); AvgFall=mean(fu_rainfall);

figure, hist(MxFall);
title('Maximum Rainfall of the Month','FontSize',10);

totalcrf=numel(fu_rainfall) for kk=1:totalcrf
if (MxFall==fu_rainfall(kk)) stamp=kk;
end end

Future_data=ndata2(:,4);

yda=Future_data(1:1000); yea=chennai_rainfall(1:1000); ya=[yda yda];
inpp=xa;
 

xa=[xa xa];
[r1 c1]=size(ya); ya=reshape(ya,[c1 r1]);

[accuracy1]=SvmAlgorithm(xa,ya); targg=yda'; [fn1,fp1,tp1,tn1]=FFANN(inpp,targg);
accuracy2 = num2str(((tp1+tn1)/(tp1+tn1+fp1+fn1))*100) Precision = num2str((tp1/(tp1+fp1))*100)
Recall	= num2str((tp1/(tp1+fn1))*100)

% % % msgbox(accuracy2);
msgbox([{'Accuracy='	accuracy2}  {'Precision='	Precision} {'Recall=' Recall}]);

maxmonth=max(Future_data); for i=1:numel(Future_data)
if Future_data(i)==maxmonth stamp=i;
end end
alldata_month=Future_data; month=alldata(:,4); showmonth=cell2mat(month(stamp)) [mname2]=monthlyPred(showmonth);
 
msgbox([mname2,{'RF=' num2str(maxmonth) 'in cm'}]);


MONTHLY PREDICTION:


function monthlyPred(ndata)

figure, AqdData=(ndata(:,3)); hist(AqdData); title('January');

figure, AqdData=(ndata(:,4)); hist(AqdData); title('February');


figure, AqdData=(ndata(:,5)); hist(AqdData); title('March');

figure, AqdData=(ndata(:,5)); hist(AqdData); title('April');

figure, AqdData=(ndata(:,5));
 
hist(AqdData); title('May');

figure, AqdData=(ndata(:,5)); hist(AqdData); title('June');

figure, AqdData=(ndata(:,5)); hist(AqdData); title('July');

figure, AqdData=(ndata(:,5)); hist(AqdData); title('August');

figure, AqdData=(ndata(:,5)); hist(AqdData); title('September');

figure, AqdData=(ndata(:,5)); hist(AqdData); title('October');

figure,
 
AqdData=(ndata(:,5)); hist(AqdData); title('November');

figure, AqdData=(ndata(:,5)); hist(AqdData); title('December');

MAIN RAINFALLPREDICTION:
clc;
clear all; close all;
warning('WARNG:Your System might be slow');

% % Read the Rainfall Dataset
[ndata, text, alldata] = xlsread('rfds.xls','rfds'); dplot=ndata(1:115,3:14);
hp=ndata(1:1,3:14)

monthlyPred(ndata); close all;
figure, surf(dplot);
title('India 1901 - 2015 Prediction','FontSize',15); pause(2);

x = inputdlg('Enter Month num') data = cell2mat(x)
 
d=str2num(data);
%
figure, AqdData=(ndata(:,d)); stem(AqdData); xlabel('Average Rainfall');

MxFall=max(AqdData); MnFall=min(AqdData); AvgFall=mean(AqdData);

fprintf('Maximum Rainfall	Registered=%d\n',uint16(MxFall)); fprintf('Minimum Rainfall Registered=%d\n',MnFall); fprintf('Average Rainfall Registered=%d\n',AvgFall);

%*******************************************
% Spatial Interpolation Step Basic
%******************************************* X = 0:10;
V = sin(X);
Xq = 0:.25:10;
Vq = interp1(X,V,Xq); plot(X,V,'o',Xq,Vq)
%*******************************************

