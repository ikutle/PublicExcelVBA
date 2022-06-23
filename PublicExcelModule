'----------------------------------------------------------------------------------
' Procedure : ResolveDisplayNameToSMTP
' Author    : Sue Mosher - updated by D.Bartrup-Cook to work in Excel late binding.
'-----------------------------------------------------------------------------------
Public Function ResolveDisplayName(sFromName) As Boolean

    Dim OLApp As Object 'Outlook.Application
    Dim oRecip As Object 'Outlook.Recipient
    Dim oEU As Object 'Outlook.ExchangeUser
    Dim oEDL As Object 'Outlook.ExchangeDistributionList

    Set OLApp = CreateObject("Outlook.Application")
    Set oRecip = OLApp.Session.CreateRecipient(sFromName)
    oRecip.Resolve
    If oRecip.Resolved Then
        ResolveDisplayName = True
    Else
        ResolveDisplayName = False
    End If

End Function

'----------------------------------------------------------------------------------
' Procedure : ResolveDisplayNameToSMTP
' Author    : Sue Mosher - updated by D.Bartrup-Cook to work in Excel late binding.
'-----------------------------------------------------------------------------------
Public Function ResolveDisplayNameToSMTP(sFromName) As String
    Dim OLApp As Object 'Outlook.Application
    Dim oRecip As Object 'Outlook.Recipient
    Dim oEU As Object 'Outlook.ExchangeUser
    Dim oEDL As Object 'Outlook.ExchangeDistributionList

    Set OLApp = CreateObject("Outlook.Application")
    Set oRecip = OLApp.Session.CreateRecipient(sFromName)
    oRecip.Resolve
    If oRecip.Resolved Then
        Select Case oRecip.AddressEntry.AddressEntryUserType
            Case 0, 5 'olExchangeUserAddressEntry & olExchangeRemoteUserAddressEntry
                Set oEU = oRecip.AddressEntry.GetExchangeUser
                If Not (oEU Is Nothing) Then
                    ResolveDisplayNameToSMTP = oEU.PrimarySmtpAddress
                End If
            Case 10, 30 'olOutlookContactAddressEntry & 'olSmtpAddressEntry
                    ResolveDisplayNameToSMTP = oRecip.AddressEntry.Address
        End Select
    End If
End Function
