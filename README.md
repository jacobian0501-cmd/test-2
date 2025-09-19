# test-2

<%@ Page Language="C#" Debug="true" AutoEventWireup="true" CodeFile="QTIME_CONTROL_ALLOW_LIST.aspx.cs" Inherits="Default_web" MaintainScrollPositionOnPostback="true" %>
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title>QTIME CONTROL ALLOW LIST</title>
	<link href="../css/bootstrap.flaty.min.css" rel="stylesheet">
    <style>
        /* 使用 CSS 設定 div 的寬度 */
        .panel-primary {
            width: 1480px;
        }

        /* 使用 CSS 設定表格邊框 */
        table {
            border-collapse: collapse;
        }
        table, th, td {
            border: 1px solid #ddd;
        }
        .GV_03_Wrapper {
            height: 300px; /* 固定高度，請自行調整 */
            overflow-y: auto; /* 加入垂直 ScrollBar */
        }
        .GV_03_Wrapper table {
            /* 保持表格寬度在 wrapper 內 */
            width: 100%;
        }
    </style>
</head>
<body>
<form id="form1" runat="server">
<div class="panel panel-primary" style="margin-top:30px;">
        <table>
			<tr>
				<td><asp:label runat="server" CssClass="label label-primary" Text="QTIME CONTROL ALLOW LIST(白名單)"
                    Style="font-size:28px"></asp:label>
				</td>
			</tr>
		</table>
        <br />
        <asp:Label ID="last_updateTime" runat="server" Font-Size="Small" /> &nbsp;&nbsp;&nbsp;
        <asp:Label ID="last_uploadTime" runat="server" Font-Size="Small" />&nbsp;&nbsp;&nbsp;
        <asp:Label ID="Label12" runat="server" Font-Size="Small" Text="網頁如有問題請call#6598"></asp:Label>
        <div>
        <table  width="100%">
			<tr>
				<td ><asp:label id="lblFunName" runat="server" CssClass="label label-default" Width="100%"  Text="QTIME CONTROL ALLOW LIST"
                     Style="font-size:14px"></asp:label></td>
                <td width="50%" align=Right>
                    工號:<asp:TextBox Height="20" ID="txt_id" MaxLength="20" runat="server" Width="80px" />		
                    密碼:<asp:TextBox ID="txt_password" Height="20" MaxLength="20" runat="server" TextMode="Password" Width="80px"/>
							 <asp:CheckBox ID="CheckBox1" Text="記住密碼" runat="server" />
                </td>
			</tr>
		</table>
        </div>
        <div>
        <table width="100%">
            <tr>
                <td width="50%">  
                    <asp:Label runat="server" Text="註冊流程 : <br/> " 
                        CssClass="label label-warning" Style="font-size:16px"></asp:Label>
                    <asp:Label runat="server" Text="1.挑出Lot後按編輯 <br/> 2.點選啟用、選擇順下/緩下、填寫MEMO <br/> 3.確認下方Qloop Status， 有整理該Qloop目前各道狀況 <br/> 4.確認OK後，點擊更新" 
                        CssClass="label-bold" Style="font-size:16px"></asp:Label>
                </td>
                <td>
                    <asp:Label runat="server" Text="說明 : <br/> " 
                        CssClass="label label-warning" Style="font-size:16px"></asp:Label>
                    <asp:Label runat="server" Text="順下- 依RTD排序，排到就run <br/> 緩下- 如下家還有issue，放到Qtime alarm再下放 <br/> END_OPE_NO(結束站點)- Lot下到這站開始恢復正常Qtime control，可空白不填" 
                        CssClass="label-bold" Style="font-size:16px"></asp:Label>
                </td>
            </tr>
            <tr>
                <td >
                    <br />
                    <asp:Label runat="server" Text="LOT註冊: " CssClass="label label-info" Style="font-size:20px"></asp:Label>

                    <asp:Label ID="Label11" runat="server" Text="QTIME起始點" Style="font-size:16px"></asp:Label>
                    <asp:DropDownList ID="ddl_06" runat="server" AutoPostBack="true" onselectedindexchanged="ddl_06_SelectedIndexChanged"></asp:DropDownList>
                    
                    <asp:Label ID="Label5" runat="server" Text="LOT_ID" Style="font-size:16px"></asp:Label>
                    <asp:DropDownList ID="ddl_05" runat="server" AutoPostBack="true" onselectedindexchanged="ddl_05_SelectedIndexChanged"></asp:DropDownList>    
                    
                </td>
            </tr>
        </table>
        </div>
        <br />
	    <asp:label id="ErrorLabel_a" runat="server" CssClass="LabelCss_ERR"  style="font-family: Arial, Helvetica, sans-serif"></asp:label>
<%--        <br />
            <div class="panel-heading">
                <h3 class="panel-title">LOT setting :</h3>
            </div>--%>
            <div class="panel-body">
            <table width="100%">
            <tr><td>
                <asp:GridView ID="GV_02" runat="server" ForeColor="#333333" BorderStyle="Inset"  
                    UseAccessibleHeader="true"
                    HeaderStyle-CssClass="thead-default"
                    CssClass="table table-striped table-hover"
                    CellPadding="6"
                    onrowcancelingedit="GV_02_RowCancelingEdit" 
                    onrowediting="GV_02_RowEditing" 
                    onrowupdating="GV_02_RowUpdating" AutoGenerateColumns="False">
                        <RowStyle Wrap="False" BackColor="#EFF3FB" Font-Names="Arial"/>
                        <Columns>
                        <asp:CommandField ShowEditButton="True" ButtonType="Button" />
                            <asp:TemplateField HeaderText="LOT_ID" SortExpression="LOT_ID">
                                <ItemTemplate>
                                    <asp:Label ID="Label1" runat="server" Text='<%# Bind("LOT_ID") %>'></asp:Label>
                                </ItemTemplate>
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="PRODSPEC_ID" SortExpression="PRODSPEC_ID">
                                <ItemTemplate>
                                    <asp:Label ID="Label3" runat="server" Text='<%# Bind("PRODSPEC_ID") %>'></asp:Label>
                                </ItemTemplate>
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="MAINPD_ID" SortExpression="MAINPD_ID" >                               
                                <ItemTemplate>
                                    <asp:Label ID="Label4" runat="server" Text='<%# Bind("MAINPD_ID") %>'></asp:Label>
                                </ItemTemplate>
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="TOP_ENTRY_OPE_NO" SortExpression="TOP_ENTRY_OPE_NO">
                                <ItemTemplate>
                                    <asp:Label ID="Label5" runat="server" Text='<%# Bind("TOP_ENTRY_OPE_NO") %>'></asp:Label>
                                </ItemTemplate>                      
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="END_OPE_NO" SortExpression="END_OPE_NO">
                                <ItemTemplate>
                                    <asp:Label ID="Labe38" runat="server" Text='<%# Bind("END_OPE_NO") %>'></asp:Label>
                                </ItemTemplate>
                                <EditItemTemplate>
                                    <asp:TextBox ID="END_OPE_NO" runat="server" Text='<%# Bind("END_OPE_NO") %>'></asp:TextBox>
                                </EditItemTemplate>
                            </asp:TemplateField>  
                            <asp:TemplateField HeaderText="CONTROL_FLAG" SortExpression="CONTROL_FLAG">
                                <ItemTemplate>
                                    <asp:Label ID="Label6" runat="server" Text='<%# Bind("CONTROL_FLAG") %>'></asp:Label>
                                </ItemTemplate>
                                <EditItemTemplate>
                                    <asp:RadioButtonList ID="CONTROL_FLAG" runat="server" 
                                        SelectedValue='<%# Bind("CONTROL_FLAG") %>'>
                                        <asp:ListItem Value="N" Text="不啟用"></asp:ListItem>
                                        <asp:ListItem Value="Y" Text="啟用"></asp:ListItem>
                                    </asp:RadioButtonList>
                                </EditItemTemplate>
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="DISPATCH_TYPE" SortExpression="DISPATCH_TYPE">
                                <ItemTemplate>
                                    <asp:Label ID="Label9" runat="server" Text='<%# Bind("DISPATCH_TYPE") %>'></asp:Label>
                                </ItemTemplate>
                                <EditItemTemplate>
                                    <asp:RadioButtonList ID="DISPATCH_TYPE" runat="server" 
                                        SelectedValue='<%# Bind("DISPATCH_TYPE") %>'>
                                        <asp:ListItem>順下</asp:ListItem>
                                        <asp:ListItem>緩下</asp:ListItem>
                                    </asp:RadioButtonList>
                                </EditItemTemplate>
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="MEMO" SortExpression="MEMO">
                                <ItemTemplate>
                                    <asp:Label ID="Label8" runat="server" Text='<%# Bind("MEMO") %>'></asp:Label>
                                </ItemTemplate>
                                <EditItemTemplate>
                                    <asp:TextBox ID="MEMO" runat="server" Text='<%# Bind("MEMO") %>'></asp:TextBox>
                                </EditItemTemplate>
                            </asp:TemplateField>                    
                            <asp:TemplateField HeaderText="CLAIM_USER" SortExpression="CLAIM_USER">
                                <ItemTemplate>
                                    <asp:Label ID="Label9" runat="server" Text='<%# Bind("CLAIM_USER") %>'></asp:Label>
                                </ItemTemplate>
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="CLAIM_TIME" SortExpression="CLAIM_TIME">
                                <ItemTemplate>
                                    <asp:Label ID="Label10" runat="server" Text='<%# Bind("CLAIM_TIME") %>'></asp:Label>
                                </ItemTemplate>
                            </asp:TemplateField>
                        </Columns>
                        <FooterStyle BackColor="#C6C3C6" ForeColor="Black" />
                        <PagerStyle BackColor="#C6C3C6" ForeColor="Black" HorizontalAlign="Right" />
                        <SelectedRowStyle BackColor="#9471DE" Font-Bold="True" ForeColor="White" />
                    </asp:GridView>  
                </td>
            </tr>
            </table>
            </div>        
        
            <div class="panel-heading">
                <h3 class="panel-title">QTIME LOOP STATUS</h3>
            </div>
            <div class="panel-body">  
            <div class="GV_03_Wrapper">    
            <table>
                <asp:GridView ID="GV_03" runat="server" AutoGenerateColumns="False" BorderStyle="Groove"
                    UseAccessibleHeader="true"
                    HeaderStyle-CssClass="thead-default"
                    CssClass="table table-striped table-hover"
                    RowStyle-HorizontalAlign="Left"
                    HeaderStyle-HorizontalAlign="Center"
                    CellPadding="4"
                    onrowdatabound="GV_03_RowDataBound">
                 <Columns>
                            <asp:BoundField DataField="DS_OPE_NO" HeaderText="DS_OPE_NO" SortExpression="DS_OPE_NO" />
                            <asp:BoundField DataField="QTIME_GRADE" HeaderText="QTIME_GRADE" SortExpression="QTIME_GRADE" />
                            <asp:BoundField DataField="PATH_CHECK" HeaderText="PATH_CHECK" SortExpression="PATH_CHECK" />
                            <asp:BoundField DataField="CAPACITY_CHECK" HeaderText="CAPACITY_CHECK" SortExpression="CAPACITY_CHECK" />
                            <asp:BoundField DataField="CAPACITY_BY_RISK_EQPG" HeaderText="CAPACITY_BY_RISK_EQPG" SortExpression="CAPACITY_BY_RISK_EQPG" />
                 </Columns>
                </asp:GridView>
            </table>
            </div>
            </div>  
        <br /> 
        <div>
        <table width="100%">
            <tr><td valign=top><table align="left" border="3" cellspacing="2" style="width:50%">
                        <tr>
                            <td height="25" bgcolor="#46A3FF"   ><b>Filter:</b></td>
                            <td bgcolor="#46A3FF">
                                <asp:DropDownList ID="DD_filterColumn" runat="server">
                                <asp:ListItem Text="LOT_ID" Value="LOT_ID"/>
                                <asp:ListItem Text="TOP_ENTRY_OPENO" Value="TOP_ENTRY_OPENO"/>
                                                           
                                </asp:DropDownlist>                 
                            </td>
                            <td bgcolor="#0066CC">
                                <asp:DropDownList ID="DD_filterCondition" runat="server">
                                <asp:ListItem Text="等於" Value="equals"/>                
                                <asp:ListItem Text="大於" Value="graterThan"/>                
                                <asp:ListItem Text="小於" Value="smallerThan"/>                
                                <asp:ListItem Text="不等於" Value="notEquals"/>                
                                <asp:ListItem Text="開頭以" Value="startWith"/>                
                                <asp:ListItem Text="結尾以" Value="endWith"/>                
                                <asp:ListItem Text="不開頭以" Value="notStartWith"/>                
                                <asp:ListItem Text="不結尾以" Value="notEndWith"/>                
                                <asp:ListItem Text="包含" Value="contain"/>                
                                <asp:ListItem Text="不包含" Value="notContain"/>                
                                </asp:DropDownlist>                  
                            </td>
                            <td bgcolor="#46A3FF"><asp:TextBox ID="txt_filter" Width="80" runat="server" /></td>
                            <td bgcolor="#46A3FF"><asp:Button ID="Btn_addCondition" Text="加入" OnClick="onClick_addCondition" Runat="server" /></td>
                            <td bgcolor="#46A3FF"><asp:Button ID="Btn_giveup_Search" Text="清除篩選" OnClick="onClick_clear_search" Runat="server" /></td>
                        </tr>
                        <tr id="showCondition" runat="Server">
                            <td colspan="5" bgcolor="#FFFFFF"><font color="#000066" size="2" face="Arial">
                                <asp:TextBox BorderStyle="none" Font-Overline="false" Font-Underline="false" ID="txt_filterCondition" runat="server" TextMode="MultiLine" Width="380" Rows="1"/>                
                            </font></td>
                            <td> <asp:Button ID="Btn_Search" Text="執行篩選" OnClick="onClick_filter" runat="server" /> </td>
                        </tr>
                    </table>
                </td>
                <td>
                    <asp:Label ID="Label14" runat="server"  Font-Size="Small" BorderStyle="Double" 
                        Text="注意事項:<br />
                              1.CONTROL_FLAG: 這筆設定是否啟用; 正常是Y(啟用)，如果是N(不啟用)，可能是LOT停太久被系統關掉，可自行再打開Y <br />
                              2.END_OPE_NO(結束站點)，可使用編輯功能去更改或刪除 <br />
                              3.資料每15分鐘更新，註冊後最多等15min會生效" >
                            
                    </asp:Label>      
                </td>
            </tr>
        </table>
        </div>
        <br />
            <div class="panel-heading">
                <h3 class="panel-title">CURRENT SETTING </h3>
            </div>
            <div class="panel-body" >
            <table width="100%">
                    <asp:GridView ID="GV_01" runat="server" 
                        AutoGenerateColumns="False"
                        CssClass="table table-striped table-hover"
                        UseAccessibleHeader="true"
                        HeaderStyle-CssClass="thead-default"
                        AlternatingRowStyle-BackColor="#f9f9f9"
                        CellPadding="5"
                        onrowcancelingedit="GV_01_RowCancelingEdit" 
                        onrowediting="GV_01_RowEditing" 
                        onrowupdating="GV_01_RowUpdating">

                     <RowStyle Wrap="False" BackColor="#EFF3FB" Font-Names="Arial"/>

                    <Columns>
                            <asp:CommandField ShowEditButton="True" ButtonType="Button" />
                        
                            <asp:TemplateField HeaderText="LOT_ID" SortExpression="LOT_ID">
                            <ItemTemplate>
                            <asp:Label ID="Label24" runat="server" Text='<%# Bind("LOT_ID") %>'></asp:Label>
                            </ItemTemplate>
                            </asp:TemplateField>
                            
                            <asp:TemplateField HeaderText="TOP_ENTRY_OPENO" SortExpression="TOP_ENTRY_OPENO">
                            <ItemTemplate>
                            <asp:Label ID="Label25" runat="server" Text='<%# Bind("TOP_ENTRY_OPENO") %>'></asp:Label>
                            </ItemTemplate>
                            </asp:TemplateField>

                            <asp:TemplateField HeaderText="END_OPE_NO" SortExpression="END_OPE_NO">
                                <ItemTemplate>
                                    <asp:Label ID="Label39" runat="server" Text='<%# Bind("END_OPE_NO") %>'></asp:Label>
                                </ItemTemplate>
                                <EditItemTemplate>
                                    <asp:TextBox ID="END_OPE_NO" runat="server" Text='<%# Bind("END_OPE_NO") %>'></asp:TextBox>
                                </EditItemTemplate>
                            </asp:TemplateField>

                            <asp:TemplateField HeaderText="OPE_NO" SortExpression="OPE_NO">
                            <ItemTemplate>
                            <asp:Label ID="Label26" runat="server" Text='<%# Bind("OPE_NO") %>'></asp:Label>
                            </ItemTemplate>
                            </asp:TemplateField>

                            <asp:TemplateField HeaderText="CONTROL_FLAG" SortExpression="CONTROL_FLAG">
                                <ItemTemplate>
                                    <asp:Label ID="Label27" runat="server" Text='<%# Bind("CONTROL_FLAG") %>'></asp:Label>
                                </ItemTemplate>
                                <EditItemTemplate>
                                    <asp:RadioButtonList ID="CONTROL_FLAG" runat="server" 
                                        SelectedValue='<%# Bind("CONTROL_FLAG") %>'>
                                        <asp:ListItem Value="N" Text="不啟用"></asp:ListItem>
                                        <asp:ListItem Value="Y" Text="啟用"></asp:ListItem>
                                    </asp:RadioButtonList>
                                </EditItemTemplate>
                            </asp:TemplateField>

                            <asp:TemplateField HeaderText="DISPATCH_TYPE" SortExpression="DISPATCH_TYPE">
                            <ItemTemplate>
                            <asp:Label ID="Label28" runat="server" Text='<%# Bind("DISPATCH_TYPE") %>'></asp:Label>
                            </ItemTemplate>
                            </asp:TemplateField>

                            <asp:TemplateField HeaderText="MEMO" SortExpression="MEMO">
                                <ItemTemplate>
                                    <asp:Label ID="Label29" runat="server" Text='<%# Bind("MEMO") %>'></asp:Label>
                                </ItemTemplate>
                                <EditItemTemplate>
                                    <asp:TextBox ID="MEMO" runat="server" Text='<%# Bind("MEMO") %>'></asp:TextBox>
                                </EditItemTemplate>
                            </asp:TemplateField>

                            <asp:TemplateField HeaderText="CLAIM_USER" SortExpression="CLAIM_USER">
                                <ItemTemplate>
                                    <asp:Label ID="Label30" runat="server" Text='<%# Bind("CLAIM_USER") %>'></asp:Label>
                                </ItemTemplate>
                            </asp:TemplateField>
                            <asp:TemplateField HeaderText="CLAIM_TIME" SortExpression="CLAIM_TIME">
                                <ItemTemplate>
                                    <asp:Label ID="Label31" runat="server" Text='<%# Bind("CLAIM_TIME") %>'></asp:Label>
                                </ItemTemplate>
                            </asp:TemplateField>
                        </Columns>

                </asp:GridView>
            </table>    
            </div>
        <table>
            <tr>
                <td>
                    <asp:Label ID="where_setting" Visible="false" runat="server" Text=""></asp:Label>
                    <asp:Label ID="where_main" Visible="false" runat="server" Text=""></asp:Label>
                    <asp:Label ID="orderBy" Visible="false" runat="server" Text=""></asp:Label>
                    <asp:Label ID="sortDirection" Visible="false" runat="server" Text=""></asp:Label>
                    <%--receive UserID--%>
                    <asp:TextBox ID="UserID" runat="server" style="display:none" Text=""></asp:TextBox>
                    <%--receive MMcheck頁面回傳值--%>
                    <asp:TextBox ID="MMuserid" runat="server" style="display:none" Text=""></asp:TextBox>
                </td>        
            </tr>          
        </table>
</div>
</form>
</body>
</html>



